> [ExamTopics: Amazon AWS Certified Solutions Architect - Associate SAA-C03 Exam](https://www.examtopics.com/exams/amazon/aws-certified-solutions-architect-associate-saa-c03)를 기반으로 학습한 내용입니다.

# Practice 01(Question #1 ~ #50)

## Question #1

### 핵심

- 장거리에서 하나의 S3버킷으로 데이터를 모으고 싶을 때

### 상황

- [Amazon S3 Transfer Acceleration](https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/userguide/transfer-acceleration.html)

  - 클라이언트와 S3 버킷 간의 *장거리 파일 전송*을 파일을 빠르고 쉽고 안전하게 전송할 수 있는 버킷 수준 기능입니다.
  - Transfer Acceleration은 전 세계에서 S3 버킷으로 전송 속도를 최적화하도록 설계되었습니다.
  - Transfer Acceleration은 Amazon CloudFront에서 전 세계에 분산된 *엣지 로케이션*을 활용합니다. 엣지 로케이션에 도착한 데이터는 최적화된 네트워크 경로를 통해 Amazon S3로 라우팅됩니다.

## Question #2

### 상황

- S3에 저장된 log를 간단하게 분석할 때

### 핵심

- [Amazon Athena](https://aws.amazon.com/ko/athena/)
  - Amazon Simple Storage Service(S3) 데이터 레이크 및 온프레미스나 SQL 또는 Python을 사용하는 기타 클라우드 시스템을 포함하는 25개 이상의 데이터 소스로부터 데이터를 분석하거나 애플리케이션을 구축합니다.

## Question #3

## 상황

- IAM이 아니라 *AWS Organizations*로 여러 계정을 관리하는 회사에서 S3특정 버킷 접근을 특정 조직에만 제한하고 싶을 때

### 핵심

- [AWS Organizations](https://docs.aws.amazon.com/ko_kr/organizations/latest/userguide/orgs_introduction.html)을 사용할 때 특정 계정에만 특정 서비스를 사용할 수 있도록 설정할 수 있는 서비스

  - AWS Organizations은 생성한 여러 AWS 계정을 조직에 통합하고 중앙에서 관리할 수 있는 계정 관리 서비스

- [S3 bucket policy의 Condition Key](https://docs.aws.amazon.com/ko_kr/organizations/latest/userguide/orgs_permissions_overview.html)

- 액션의 조건을 지정할 수 있는 키
  - `aws:PrincipalOrgID` : AWS Organizations 조직의 ID
    - 가장 최적의 방법
    - 리소스 기반 정책의 Principal 요소 지정을 `간소화`합니다. 조직의 멤버인 모든 계정을 나열하는 대신 Condition 요소에 `조직 ID`를 지정할 수 있다.
  - `aws:PrincipalOrgPaths` : AWS Organizations 조직의 경로
    - 가능하나 오버헤드, 복잡성이 증가
    - 특정 조직 루트, OU 또는 해당 하위 항목의 `멤버`를 일치시킨다. 요청을 수행하는 보안 주체(루트, IAM 사용자 또는 역할)가 지정된 조직 경로에 있는 경우 true를 반환한다.
  - `aws:PrincipalTag` : AWS Organizations 조직의 태그
    - 가능하나 오버헤드, 복잡성이 증가
    - 유저에 일일이 태그 붙이고 그 태그를 버킷 정책에 추가해야 한다.

## Question #4

### 상황

- VPC 안 EC2에서 서비스가 작동하고 있음. 인터넷을 직접 연결하지 않고 프라이빗 네트워크를 통해 외부 S3에 접근하고 싶을 때(S3에는 서비스가 처리해야할 log가 저장되어 있음)

### 핵심

- [VPC endpoint](https://docs.aws.amazon.com/vpc/latest/privatelink/concepts.html#concepts-endpoint-services)
- VPC Endpoint는 퍼블릭 인터넷을 사용하지 않고, 프라이빗 네트워크를 통해 AWS 서비스들을 연결할 수 있게 해준다.

## Question #5

### 상황

- 다른 가용영역에서 비슷한 서비스를 운영하고 있다. 유저가 두 가용역역에 있는 EC2-EBS에 저장된 자신의 데이터를 **동시에** 볼 수 있도록 하는 방법을 찾고 있다.

### 핵심

- 하나의 EC2에만 할당될 수 있는 기본 EBS(EBS io1, io2 제외)의 한계를 극복하기 위해 EFS를 사용한다.
- [EFS(Amazon Elastic File System)](https://aws.amazon.com/ko/efs/)
  - 여러 EC2 인스턴스에서 동시에 사용할 수 있는 파일 스토리지 서비스
  - cross AZ, cross region을 지원한다.

## Question #6

### 상황

- 온프레미스 환경의 NFS에서 S3로 최소한의 네트워크 대역폭을 사용하면서 가능한 빨리 `대용량 데이터`를 옮기고 싶다. 용량은 70TB이며 데이터는 더이상 늘어나지 않는다.
  - `NFS(Network File System)`: 네트워크에 파일을 저장하는 메커니즘

### 핵심

- [AWS Snowball Edge](https://docs.aws.amazon.com/ko_kr/snowball/latest/developer-guide/whatisedge.html)
  - 기기를 사용하여 대량의 데이터를 AWS로 전송하고 AWS에서 데이터를 처리한 다음 기기를 사용하여 데이터를 다운로드할 수 있다.
  - 물리적 전송을 사용하여 대역폭을 최소화할 수 있다.

## Question #7

### 상황

- 메시지 분산 및 스케일링

### 핵심

- [SQS](https://docs.aws.amazon.com/ko_kr/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)

  - 내구력 있고 가용성이 뛰어난 보안 호스팅 대기열을 제공하며 이를 통해 분산 소프트웨어 시스템과 구성 요소를 통합 및 **분리**할 수 있다.

- [SNS](https://docs.aws.amazon.com/ko_kr/sns/latest/dg/welcome.html)
  - 게시자에서 구독자(생산자 및 소비자라고도 함)로 메시지를 전송하는 관리형 서비스
- [`하나의 SNS + 여러 개의 SQS`]를 통해 *Fan Out Pattern*을 구현하면 많은 양의 메세지를 처리할 수 있다.

## Question #8

### 상황

- 기존 레거시 플랫폼은 여러 컴퓨터 노드에서 작업을 조정하는 기본 서버로 구성되어있다(분산). AWS로 마이그레이션을 하는 상황. 탄력성과 확장성을 최대화 하기 위한 솔루션을 묻고 있다.

### 핵심

- SQS를 통해 작업 큐를 만들고 큐 사이즈에 맞게 EC2 인스턴스를 늘리고 줄인다.
- SQS
  - SQS하면 디커플링!
- [Auto Scaling](https://docs.aws.amazon.com/ko_kr/autoscaling/ec2/userguide/auto-scaling-groups.html)

## Question #9

### 상황

- 회사가 SMB 파일 서버를 데이터 센터에서 운영하고 있다. SMB 파일은 새로 만들어진 지 몇일 동안은 지속적으로 요청된다. 하지만 일주일 후에는 거의 요청되지 않는다. 그리고 이 파일들의 용량이 회사의 데이터 센터의 용량을 초과하려 한다. 이 상황에서 지연 시간을 줄이고 가용성을 높이면서 파일 생애주기를 관리하고 싶다.

### 핵심

- [Amazon S3 File Gateway](https://docs.aws.amazon.com/ko_kr/filegateway/latest/files3/what-is-file-s3.html)
  - S3와 온-프레미스 간에 데이터를 주고받을 수 있도록 해주는 서비스
  - NFS와 SMB 프로토콜을 사용하여 접근 가능하게 설정된 S3 버킷
  - 최근에 사용한 데이터를 File Gateway 내에 캐시할 수 있다.
  - 라이프사이클 정책으로 S3 Glacier로 전환할 수 있다.

## Question #10

### 상황

- 이커머스 회사에서 API 요청을 받은 순서대로 처리하고 싶을 때

### 핵심

- [SQS FIFO](https://docs.aws.amazon.com/ko_kr/AWSSimpleQueueService/latest/SQSDeveloperGuide/FIFO-queues.html)
  - 표준 대기열의 모든 기능을 갖추고 있지만 작업 및 이벤트의 순서가 중요하거나 중복을 허용할 수 없는 경우 애플리케이션 간 메시징을 향상시키도록 설계

## Question #11

### 상황

-

### 핵심

-
