public void dfs(int root,int length,Deque<Integer> path){
	//出口
	if(root == length)
		return ;
	//决策树
	for(int i=0;i<length;i++){
		//小剪枝
		if(path.contains(i))
			continue；
		//大剪枝
		if()
			break；
		//选择节点
		path.add(i);
		//循环
		dfs(root+1,length;path);
		//回溯
		path.removelast();
	}
	
}

