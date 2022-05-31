# FancyTree
조직도를 생성하는데 사용

## Classes (객체, Object)
---

<br>

**Fancytree**

fancyTree를 나타내는 tree object를 의미 (tree자체를 제어)


<br><br>

**FancytreeNode**

Tree에서 각각 나뉘어지는 노드를 나타내는 객체



<br><br><br>

## FancyTree API





<br><br><br>
<br><br><br>

**Initilization**
---

## Options

### Data Loading

option set : 'selectMode: 3' & 'lazyLoad: function() {}' 일 경우, 필요한 node를 load하기 전까지 node의 children에 접근할 수 없음.

node.load() - 비동기 통신이기 때문에 반환받은 $.Promise 객체를 통해 node.getChildren() (or node.children)에 접근




<br><br><br>

### Events

- click : 


<br><br><br>
<br><br><br>

<br><br><br>
<br><br><br>

### [참고] <br>
  * Document <br>
  *-* 예시 & 연습 (example) - http://wwwendt.de/tech/fancytree/demo/index.html#welcome.html <br>
  *-* project home - https://github.com/mar10/fancytree/ <br>
  *-* introduction of Fancytree - https://github.com/mar10/fancytree/wiki/ <br>

  * 객체 및 API
  *-* Fancytree Doc - https://wwwendt.de/tech/fancytree/doc/jsdoc/Fancytree.html <br>
  *-* FancytreeNode Doc - https://wwwendt.de/tech/fancytree/doc/jsdoc/FancytreeNode.html <br>

  <br>

  Options <br>
  ---
  
  * Initialization - Data Loading
  *-* fancyTree load data doc (source, lazyLoad) [Official] - https://github.com/mar10/fancytree/wiki/TutorialLoadData <br>
  *-* load all nested children on select (using lazyLoading) [stackoverflow] - https://stackoverflow.com/questions/25374378/fancytree-load-all-nested-children-on-select <br>

  * Events
  *-* fancyTree click option 활용법(stackoverflow) - https://stackoverflow.com/questions/34345757/clicking-on-title-or-radio-button-to-select-fancytree-node <br>
  
