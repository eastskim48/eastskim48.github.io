---
layout: post
title: Knoweldge Graphs[1부]
category: Off-the-cuffs
excerpt_separator:  <!--more-->
comments: true
---

이 글은 [Knowledge Graphs](https://arxiv.org/pdf/2003.02320.pdf)를 참고하여 서술했습니다.  

## Knowledge graph의 정의
어떤 분야던, Technical Term을 명확하게 아는 것은 중요하다.  
**정의**는 개념을 한정하는 역할을 하기 때문이다.  
Knowledge Graph에 있어 어떤 **정의**를 따르는 경우,   
그 정의에 부합하지 않는 data graph는 Knowledge Graph라 할 수 없기 때문이다.  
Knowledge Graph에서는 Entity와 Relationship이 따라야 할 스키마 (Ontology)의 존재 여부,  
기존의 지식을 바탕으로 새로운 지식 유도 (추론) 가능 여부,  
그래프의 형태 (labeled graph, property graph)에 따른 구분 여부를  
Knowledge Graph를 정의하는 데 있어 포함시킬지가 주 논쟁거리였다.  
아래에는 서로 다른 Research paper들에서 Knowledge Graph를 정의하려 했던 여러 시도들을 정리해 보았다.
### 일반적인 정의
Real world의 지식을 모아서 쌓아놓는 것이 목적인 그래프 형태의 데이터.  
그래프에서의 node는 어떤 실재하는 개체를, edge는 개체 사이의 관계를 나타낸다.  
### Google Knowledge Graph에서의 정의
Real World에서의 Entity와, 그들 사이의 관계를 이해하도록 설계된 그래프
### 그 외, Knowledge Graph를 정의하려는 여러 시도들
- Graph where nodes represent entities, and edges represent relationships between those entities [구조로써의 정의]
- Graph structured Knowledge Base [지식 저장소로써의 정의]
- Mainly describes real world entities and their interrelationships, organized in a graph;
  defines possible classes and relations of entities in a schema;
  allow for potentially interrelating arbitrary entities with each others;
  covers various topical domains [체계(스키마)가 존재하고, 객체는 그 체계를 따라야 한다]
- A knowledge graph acquires and intergrates information into an ontology and applies a reasoner to derive new knowledge [Ontology(체계)를 따르는 지식의 형태로 정보를 저장하고, 저장한 지식에 기반해 새로운 지식을 추론할 수 있어야 한다]
- Knowledge Graph는 semi-structured data model로, Rule에 의한 추론 능력을 가진 Knowledge Based이다.

## Graph의 형태
앞서 서술했듯, Knowledge Graph를 정의하는 방식은 여러가지이지만,  
**이 글에서는 가장 보편적으로 사용되는 RDF방식의 Knolwedge Graph를 중심으로 서술하려고 한다.**  

### Directed edge-Labeled graph
- 세상의 다양한 지식들을 표한하려면, Knowledge Graph의 여러 Entity는 서로 구분된 의미를 지녀야 한다.
따라서 Node(Entity)는 구분자로서의 Label을 가진다.  
- 서로 연결된 Entity들의 조합은 다양하기 때문에, (Entity A - Entitiy B, Entitiy B - Entity C ...)
이들 사이의 관계들 또한 다양하고 구분되어야 한다.
따라서 Edge(relationship)또한 Label을 가진다.
- 철수가 영희를 좋아한다고 해서 영희도 철수를 좋아하지는 않을 수 있다.
이들 둘 사이를 "좋아함"이라는 관계로 엮기에는 무리가 있다.
따라서 Edge(relationship)은 방향성을 가지는 Directed Edge여야 한다.
이처럼 표현력을 넓히기 위해 Knowledge graph는 Directed Edge-Labeled Graph의 형태로 구현된다.  

### RDF
#### 정의
RDF는 Resource Description Framework의 약자로,  
W3C에서 정의한, 정보 자원의 구조를 표현하기 위한 **언어**이다.  
우리는 우리가 알고 있는 지식을, 다른 사람이 이해할 수 있도록 한국어라는 언어로 표현한다.  
마찬가지로 기계가 해독할 수 있도록 지식을 표현하는 데에는 RDF라는 언어를 사용한다.  

#### Semantic Web
RDF는 Semantic Web을 위한 언어로써 개발되었다.  
Semantic Web은 기계가 "의미"를 해독할 수 있는 웹 환경을 의미하는 개념이다.  
지금 우리가 보고 있는 웹 브라우저는 웹 문서를 파싱하고 렌더링하여 시각화된 형태로 보여주지만,  
각 태그 안의 데이터가 가지는 의미를 보여주지는 못한다.  
가령, "Knowledge Graph"라는 텍스트가 html 파일에서 h1태그로 둘러싸여 있으면 웹 문서에서의 '제목'으로 사용된다는 것은 알 수 있지만  
"Real world의 Entity와 그들 사이의 관계를 Edge로 표현한 그래프 형태의 데이터"를 의미하는지는 알 수 없다.

#### Linked Data
Semantic Web은, Linked Data 개념과 떼어놓을 수 없다.  
웹 환경에서 방대한 지식은 하나의 컴퓨터에 저장되어 있을 수 없고, 그렇게 되어있지도 않다.  
따라서 데이터들은 여러 위치에 분산되어 있는데,  
이러한 웹상의 데이터들을 연결된 상호 연결된 웹 환경을 지향하는 것이 Linked Data이다.   
Knowledge Graph도 마찬가지로, 방대한 Knowledge들이 분산되어 저장되어 있을 수 있다.  
이러한 분산된 데이터들이 공통된 표현 언어로 기술되고,  
각 데이터 객체들이 고유의 식별자를 통해 구분된다면  
Semantic한 의미 해석에도, 정보 검색에도 매우 유리하다.  

#### 구조
위와 같은 탄생 배경을 가지는 RDF 언어는, 다음과 같은 기본 구조를 가진다.
- 표현하려고 하는 것은 "문장"이다.
- 기본적으로 (주어(subject), 술어(predicate), 목적어(object))의 triple 형태로 기술된다. (한국식 영어 문법을 배운 사람이라면 아는, 3형식 문장과 유사하다)
- 술어는 주어에서 목적어 방향으로의 방향성을 가진다
- 서술어는 주어와 목적어와의 관계를 기술하기도 하고, 목적어가 "값"을 나타낸다면 데이터(주어)가 가지는 "값"의 의미를 기술하기도 한다. (OWL에서의 data property에 해당)
  - ex) 동섭(주어)의 나이(서술어)는 28 (목적어[값])
- (Subject, Predicate, Object)[RDF] <-> (Entity, Relationship, Entity)[Knowledge Graph] <-> (Node, Edge, Node)[Graph Structure]
- 각 Entity(주어, 목적어)는 고유의 식별자 (URI)를 가진다.
- 한국어와 한글은 다르다. 한국어를 사용하지 않는 찌아찌아족도 찌아찌아어를 기록할 때에는 한글을 사용한다.
  마찬가지로 RDF가 표현 방식을 나타내는 한국어와 같은 언어라면, RDF를 기술하는 언어는 따로 존재한다.
  - XML
    - 요새는 json으로 많이 대체되었지만, 한때 가장 핫했던 마크업 언어 형태의 데이터 포멧이다. (요새도 안드로이드 등지에서 많이 쓰인다.)
  - json-ld
    - 보편적으로 많이 쓰이는 json으로 linked data를 인코딩하는 방식이다.
  - RDFa
    - RDF in Attribute의 약자로, HTML 마크업 태그의 Attribute 형태로 RDF를 표현하는 방식이다.
  - Turtle
    - rdf 데이터를 저장할 때 가장 보편적으로 사용되는 포멧이다. 이유는 심플해서(?)
- 이러한 RDF의 형태는 그래프 구조의 관점에서 본다면 Directed Edge-labeled Graph이다.

#### 요약
RDF 방식의 Knowledge Graph는, RDF 언어로 지식을 표현하며,  
이를 Turtle, XML등의 형태로 저장한다.  
그래프 구조적으로는 Directed Edge-labeled Graph의 형태이다.




 

