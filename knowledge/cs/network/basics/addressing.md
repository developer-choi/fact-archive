---
tags: [network, addressing, mac, ip, dns]
---

# Questions
- [What's the MAC address?](#whats-the-mac-address)
  - [What's the difference between Physical Address and Network Address?](#whats-the-difference-between-physical-address-and-network-address)
  - [Why do we need a Physical Address(MAC) if we already have a Logical Address(IP) for communication?](#why-do-we-need-a-physical-addressmac-if-we-already-have-a-logical-addressip-for-communication)
  - [Considering MAC addresses are globally unique, why is an IP address required for routing?](#considering-mac-addresses-are-globally-unique-why-is-an-ip-address-required-for-routing)
- [How are hosts identified within a network?](#how-are-hosts-identified-within-a-network)
- [What is a hostname, and how is it resolved to a network address?](#what-is-a-hostname-and-how-is-it-resolved-to-a-network-address)

---

# Answers

## What's the MAC address?
### Official Answer
A MAC address is a **unique identifier** assigned to a network interface controller (NIC) for use as a network address in communications within a network segment.

MAC addresses are primarily assigned by device manufacturers, and are therefore often referred to as a physical address.

### Reference
- https://en.wikipedia.org/wiki/MAC_address

---

## What's the difference between Physical Address and Network Address?
### AI answer
MAC Address가 넓은 의미에서는 Network Address가 맞긴하지만,

정확하게 구분한다면 Mac Address는 Physical Address라고 부르고,

IP Address를 Network Address라고 부른다.

### Reference
- https://en.wikipedia.org/wiki/MAC_address
- https://en.wikipedia.org/wiki/IP_address

---

## Why do we need a Physical Address(MAC) if we already have a Logical Address(IP) for communication?

### AI & User Interpretation
정확한 대상에게 전달할 수 없는 문제가 발생합니다.

IP 주소(Logical Address)는 계층적(Hierarchical) 구조를 가집니다.

이는 마치 우편 주소와 같아서 국가, 시, 구, 동 순으로 범위를 좁혀가며 경로를 찾을 수 있게 해줍니다.

그래서 한계가 있습니다. 범위를 좁힐 수는 있어도 정확한 대상에게 전달할 수 없습니다.

IP주소는 위치는 알아도 대상은 알 수 없기 때문입니다.

IP가 **'현재 살고 있는 집 주소'**라면, MAC은 그 집에 사는 **'사람의 주민등록번호'**입니다.

주소는 이사 가면 바뀌지만(논리적), 사람의 고유 번호는 바뀌지 않습니다(물리적).

최종 배달 단계에서는 문 앞까지 찾아간 뒤(IP), "주민번호 ABCDE인 분 계신가요?"라고 확인(MAC)해야 정확한 전달이 완료됩니다.

---

## Considering MAC addresses are globally unique, why is an IP address required for routing?

### AI & User Interpretation

#### 주소와 주민번호로 비유하기
주민번호가 한국에서 유일하니 집 주소가 필요없는지 라는 주제입니다.

주민번호가 A인 사람이 주민번호가 B인 사람에게 물건을 보내려면,

6천만 인구를 직접 한명한명 찾아가서 주민번호가 B인지를 대조해야합니다.

1. 근데 사람의 위치는 항상 바뀐다는 문제가 있고, 
2. 6천만의 주민번호 테이블을 들고있어야 하기 때문에

물리적으로 불가능합니다.

핵심은, 주민번호는 식별자 이며, 위치를 나타내지 못한다는 점입니다.

바로 그 위치를 나타내기 위해, 주소가 필요합니다.

주민번호 = MAC 주소

주소 (서울시 무슨구 무슨동 어느아파트 몇동 몇호) = IP

주소에서 시-도 를 먼저 보고 한번 분류하고, 그 다음 구-동을 보고 또 한번 분류하듯

IP 주소도 계층적인 구조로 되어있습니다.

이를 통해 라우팅 테이블의 크기를 줄이면서도 빠르게 찾아갈 수 있게 됩니다.
- 시-도 종류만 모아놓은 라우팅 테이블을 만들고
- 그 아래 구-동 만 모아놓은 라우팅 테이블을 시-도 종류마다 1개씩 각 라우터마다 만들고

이런 식입니다.

#### 기술적인 용어 풀이
**계층적 구조와 경로 요약**

MAC 주소는 식별자 입니다.

전 세계의 모든 기기가 MAC 주소로만 통신한다면, 인터넷의 모든 라우터는 지구상의 모든 기기에 대한 경로를 개별적으로 저장해야 합니다.

이는 라우팅 테이블 크기가 증가하여 하드웨어적 한계를 초래합니다.

반면 IP 주소는 계층적(Hierarchical) 구조를 가집니다. 라우터는 특정 '네트워크 대역(Prefix)' 정보만 관리하는 **경로 요약(Route Summarization)**을 수행합니다.

이를 통해 라우팅 테이블의 크기를 획기적으로 줄여 인터넷 전체의 확장성을 보장합니다.

**논리적 추상화와 이동성**

IP 주소는 **논리적 주소(Logical Address)**로서 물리적 계층(Layer 2)과 하드웨어에 독립적입니다.

만약 MAC 주소만으로 라우팅을 수행한다면, 기기가 이동하여 네트워크 환경이 바뀔 때마다 전 세계의 모든 라우터에 해당 기기의 새로운 위치를 업데이트해야 합니다.

IP 체계에서는 기기가 속한 네트워크가 바뀌면 해당 네트워크의 IP를 새로 할당받음으로써, 전 세계 라우터들이 상위 네트워크 대역 정보만으로도 데이터를 정확히 전달할 수 있게 하는 **추상화(Abstraction)**를 제공합니다.

**브로드캐스트 도메인의 물리적 차단**

MAC 주소를 통한 장치 검색은 브로드캐스트(Broadcast) 혹은 **플러딩(Flooding)**에 의존합니다.

레이어 2 수준의 통신은 라우터를 통과할 수 없도록 설계되어 있습니다.

만약 모든 네트워크가 하나의 MAC 체계로 묶인다면, 수십억 개의 기기가 뿜어내는 브로드캐스트 패킷으로 인해 전 세계 네트워크가 마비됩니다.

IP 라우팅은 네트워크를 세그먼트 단위로 분리하여 이러한 트래픽을 관리 가능한 범위 내로 제한합니다.

---

## How are hosts identified within a network?
### Official Answer
Within a computer network, hosts are identified by [network addresses](https://en.wikipedia.org/wiki/Network_address), which allow [networking hardware](https://en.wikipedia.org/wiki/Networking_hardware) to locate and identify hosts.

> AI Annotation: 여기서 말하는 Network Address는 주로 **IP Address**(논리적 주소)와 **MAC Address**(물리적 주소)를 의미합니다. 라우터(L3 장비)는 IP 주소를 보고 최적의 경로를 찾아주며(Routing), 스위치(L2 장비)는 MAC 주소를 보고 정확한 장치를 식별(Identify)하여 데이터를 전달합니다.

> User Annotation: IP, MAC 말고도 포트 번호나 서비스 ID 등 식별 수단은 상황에 따라 더 다양할 수 있음.

### Reference
- https://en.wikipedia.org/wiki/Network_address

---

## What is a hostname, and how is it resolved to a network address?
### Official Answer
Hosts may also have [hostnames](https://en.wikipedia.org/wiki/Hostname), memorable labels for the host [nodes](https://en.wikipedia.org/wiki/Node_(networking)), which can be mapped to a network address using a [hosts file](https://en.wikipedia.org/wiki/File) or a name server such as [Domain Name Service](https://en.wikipedia.org/wiki/Domain_Name_Service).

> AI Annotation: 컴퓨터가 이름을 주소로 변환할 때 거치는 순서는 다음과 같습니다.
> 1. **Local Cache/Hosts File**: 컴퓨터는 먼저 자기 자신(로컬)에게 물어봅니다. (`/etc/hosts` 파일 확인)
> 2. **DNS Server**: 로컬에 정보가 없다면 외부의 네임 서버(DNS)에 물어봅니다.

### Reference
- https://en.wikipedia.org/wiki/Hostname
- https://en.wikipedia.org/wiki/Domain_Name_Service
