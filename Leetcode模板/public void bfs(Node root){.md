public void bfs(Node root){

```java
//定义队列,添加队头
Queue<Node> queue = new LinkedList();
queue.add(root);
//层次计数
int depth = 0;

while(!queue.isEmpty()){
	depth++;
	int size() = queue.size();	
	//遍历当前层次的所有节点
	while(size-->0){
		//访问当前层次的节点
		Node curNode = queue.poll();
		//寻找curNode的子节点，将子节点添加到队列中
		for(){}
		queue.add(......);
	}
	
}
```

}