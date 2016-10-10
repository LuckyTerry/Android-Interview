#1.ͼ�Ķ���

 ����ͼG���ɶ��������ϣ��Լ�����֮��Ĺ�ϵ��ɣ�����ļ��ϼ�ΪV������֮��Ĺ�ϵ���ɱߵļ���E��G=(V,E).

���������ͼ��ÿ���߹涨һ��������ô�õ���ͼ��Ϊ**����ͼ**�����Ҳ��Ϊ����ߡ�������ͼ�У���һ���ڵ�������ı��г��ߺ����֮�֣�����һ������߹�����������Ҳ��ʼ����յ�֮�֡��෴����û�з����ͼ��Ϊ**����ͼ**��

#��.ͼ�Ĵ洢

����һ��ͼ�Ĵ洢�����ַ�ʽ
����
����1)�ڽӱ���Ҫ����һ��˳��洢�Ķ�����ÿ�������ϵıߵ����ӱ�
����
����2)���ھ�����һ�����������ֱߵ����
��������

![����дͼƬ����](http://img.blog.csdn.net/20160613103617205)��

��ͼչʾ�����ֱ�ʾ�������ͼ�ķ�����

![����дͼƬ����](http://img.blog.csdn.net/20160613103702050)��

#��.ͼ�ı���

�����١�DFS��Depth First Search���������������Ϊÿ����������һ�������ʱ�־�������Ƚ�ͼ��ÿ������ķ��ʱ�־��Ϊ FALSE,  ֮������ͼ��ÿ�����㣬���δ�����ʣ����Ըö���Ϊ��ʼ�㣬���б�����

��������ǰ���ʵĶ�����ڽӶ�����δ�����ʵģ�����ѡһ������֮����֮���˻ص�������ʹ��Ķ��㣻ֱ������ʼ������ͨ��ȫ�����㶼������ϣ�

> ����ͼ�Ĺ���ʵ�����Ƕ�ÿ������������ڽӵ�Ĺ��̣����ķѵ�ʱ��ȡ���������õĴ洢�ṹ��
��ͼ�е�ÿ�������������1��DFS�㷨����Ϊһ��ĳ�������ѷ��ʹ������ٴ�����������������

> �ڽ������ʾ������ÿ��������ڽӵ�����ʱ��ΪO(e)��eΪ��(��)�����㷨ʱ�临�Ӷ�ΪO(n+e)

> �����ʾ������ÿ��������ڽӵ�����ʱ��ΪO(n2)��nΪ���������㷨ʱ�临�Ӷ�ΪO(n2)


�����ڡ�BFS��Breadth First Search��������ȱ�������ͼ��ĳһ���������������η��ʸý��������ڽӶ��� Vi1, Vi2, ��, Vin �ٰ���Щ���㱻���ʵ��Ⱥ�������η������������ڽӵ�����δ�����ʵĶ��㣬�ظ��˹��̣�ֱ�����ж����������Ϊֹ��

##��.���������루�ڽӾ���

���� 

```
// �ڽӾ���洢ͼ
public class Graph {
    // ������
    private int number = 9;
    // ��¼�����Ƿ񱻷���
    private boolean[] flag;
    // ����
    private String[] vertexs = { "A", "B", "C", "D", "E", "F", "G", "H", "I" };
    // ��
    private int[][] edges = { 
            { 0, 1, 0, 0, 0, 1, 1, 0, 0 }, 
            { 1, 0, 1, 0, 0, 0, 1, 0, 1 }, 
            { 0, 1, 0, 1, 0, 0, 0, 0, 1 },
            { 0, 0, 1, 0, 1, 0, 1, 1, 1 },
            { 0, 0, 0, 1, 0, 1, 0, 1, 0 }, 
            { 1, 0, 0, 0, 1, 0, 1, 0, 0 },
            { 0, 1, 0, 1, 0, 1, 0, 1, 0 },
            { 0, 0, 0, 1, 1, 0, 1, 0, 0 }, 
            { 0, 1, 1, 1, 0, 0, 0, 0, 0 } 
            };

    // ͼ����ȱ�������(�ݹ�)
    void DFSTraverse() {
        flag = new boolean[number];
        for (int i = 0; i < number; i++) {
            if (flag[i] == false) {// ��ǰ����û�б�����
                DFS(i);
            }
        }
    }

    // ͼ��������ȵݹ��㷨
    void DFS(int i) {
        flag[i] = true;// ��i�����㱻����
        System.out.print(vertexs[i] + " ");
        for (int j = 0; j < number; j++) {
            if (flag[j] == false && edges[i][j] == 1) {
                DFS(j);
            }
        }
    }

    // ͼ�Ĺ�ȱ�������
    void BFSTraverse() {
        flag = new boolean[number];
        Queue<Integer> queue = new LinkedList<Integer>();
        for (int i = 0; i < number; i++) {
            if (flag[i] == false) {
                flag[i] = true;
                System.out.print(vertexs[i] + " ");
                queue.add(i);
                while (!queue.isEmpty()) {
                    int j = queue.poll();
                    for (int k = 0; k < number; k++) {
                        if (edges[j][k] == 1 && flag[k] == false) {
                            flag[k] = true;
                            System.out.print(vertexs[k] + " ");
                            queue.add(k);
                        }
                    }
                }
            }
        }
    }

    public static void main(String[] args) {
        Graph graph = new Graph();
        System.out.println("-----------DFS-----------------");
        graph.DFSTraverse();
        System.out.println();
        System.out.println("-----------BFS-----------------");
        graph.BFSTraverse();
    }
}
```

���н����

![����дͼƬ����](http://img.blog.csdn.net/20160613112121895)��

#4.��С������prim�㷨

�����ӵ�һ���㿪ʼ������ķ�㷨�������²������������������������Ŀ��ֱ���鼰��ͨͼ�����ж��㡣

1. ���룺һ��**��Ȩ��ͨͼ**�����ж��㼯��ΪV���߼���ΪE��

2. ��ʼ����Vnew = {x}������xΪ����V�е���һ�ڵ㣨��ʼ�㣩��Enew = {}��

3. �ظ����в�����ֱ��Vnew = V��

  3.1 �ڼ���E��ѡȡȨֵ��С�ıߣ�u, v��������uΪ����Vnew�е�Ԫ�أ���v����V��û�м���Vnew�Ķ��㣨��������ж�������ǰ��������������ͬȨֵ�ıߣ��������ѡȡ����֮һ����
3.2 **��v���뼯��Vnew**�У�����u, v�����뼯��Enew�У�

4. �����ʹ�ü���Vnew��Enew���������õ�����С��������

> ��Ϊԭʼ�ļ�Ȩ��ͨͼ��ÿ����һ������ִ�����Ȩֵ��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Prim_Algorithm_0.svg/200px-Prim_Algorithm_0.svg.png)

> ����D������ѡΪ��ʼ�㡣����A��B��E��Fͨ����������D������A�Ǿ���D����Ķ��㣬��˽�A����Ӧ��AD�Ը�����ʾ��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/5/56/Prim_Algorithm_1.svg/200px-Prim_Algorithm_1.svg.png)

> ��һ������Ϊ����D��A����Ķ��㡣B��DΪ9����AΪ7��EΪ15��FΪ6����ˣ�F��D��A�������˽�����F����Ӧ��DF�Ը�����ʾ��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f5/Prim_Algorithm_2.svg/200px-Prim_Algorithm_2.svg.png)

> �㷨�����ظ�����Ĳ��衣����AΪ7�Ķ���B��������ʾ��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b4/Prim_Algorithm_3.svg/200px-Prim_Algorithm_3.svg.png)

> �ڵ�ǰ����£�������C��E��G�����ѡ��C��BΪ8��E��BΪ7��G��FΪ11��E�������˽�����E����Ӧ��BE������ʾ��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Prim_Algorithm_4.svg/200px-Prim_Algorithm_4.svg.png)

> ����ɹ�ѡ��Ķ���ֻ��C��G��C��EΪ5��G��EΪ9����ѡȡC�������ECһͬ������ʾ��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Prim_Algorithm_5.svg/200px-Prim_Algorithm_5.svg.png)
 
 

> ����G��Ψһʣ�µĶ��㣬����FΪ11����EΪ9��E������ʸ�����ʾG����Ӧ��EG��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/9/99/Prim_Algorithm_6.svg/200px-Prim_Algorithm_6.svg.png) 

> ���ڣ����ж�����ѱ�ѡȡ��ͼ����ɫ���ּ�Ϊ��ͨͼ����С���������ڴ����У���С��������Ȩֵ֮��Ϊ39��

![����дͼƬ����](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b9/Prim_Algorithm_7.svg/200px-Prim_Algorithm_7.svg.png)

##4.1 java����ʵ��

����

```
public class Prim {
	//��㼯
	public static List<Vertex> vertexList = new ArrayList<Vertex>();
	//�߼�
	public static List<Edge> EdgeList = new ArrayList<Edge>();
	//�Ѿ����ʹ��Ľ�㼯
	public static List<Vertex> containVertexList = new ArrayList<Vertex>();
	
	public static void main(String[] args) {
		primTree();
	}
	public static void primTree(){
		//��ʼ��ͼ
		buildGraph();
		//��ʼ��
		Vertex start = vertexList.get(0);
		containVertexList.add(start);
		for(int n=0;n<vertexList.size()-1;n++){
			//��ʱ�ڵ�a
			Vertex temp = new Vertex(start.key);
			Edge tempedge = new Edge(start,start,1000);
			
			for(Vertex v : containVertexList){
				for(Edge e : EdgeList){
					//�ҳ�������С��
					if(e.start==v && !containVertex(e.end)){
						if(e.Len<tempedge.Len){
							temp = e.end;
							tempedge = e;
						}
					}
				}
			}
			//�Ѹõ����
			containVertexList.add(temp);
		}
		
		//��ӡ���
		Iterator it = containVertexList.iterator();
		while(it.hasNext()){
			Vertex v =(Vertex) it.next();
			System.out.println(v.key);
		}
	}
	
	public static void buildGraph() {
		Vertex v1 = new Vertex("a");
		Prim.vertexList.add(v1);
		Vertex v2 = new Vertex("b");
		Prim.vertexList.add(v2);
		Vertex v3 = new Vertex("c");
		Prim.vertexList.add(v3);
		Vertex v4 = new Vertex("d");
		Prim.vertexList.add(v4);
		Vertex v5 = new Vertex("e");
		Prim.vertexList.add(v5);
		addEdge(v1, v2, 6);
		addEdge(v1, v3, 7);
		addEdge(v2, v3, 8);
		addEdge(v2, v5, 4);
		addEdge(v2, v4, 5);
		addEdge(v3, v4, 3);
		addEdge(v3, v5, 9);
		addEdge(v5, v4, 7);
		addEdge(v5, v1, 2);
		addEdge(v4, v2, 2);
	}
	public static void addEdge(Vertex a, Vertex b, int w) {
		Edge e = new Edge(a, b, w);
		Prim.EdgeList.add(e);
	}
	public static boolean containVertex(Vertex vte){
		for(Vertex v : containVertexList){
			if(v.key.equals(vte.key))
				return true;
		}
		return false;
	}
}
class Vertex {
	String key;
	Vertex(String key){
		this.key = key;
	}
}
class Edge{
	Vertex start;
	Vertex end;
	int Len;
	Edge(Vertex start,Vertex end,int key){
		this.start = start;
		this.end  = end;
		this.Len = key;
		
	}
}
```

#��.Dijkstra�㷨

����ʹ����**�����������**����Ǹ�Ȩ����ͼ��**��Դ���·��**���⣬�㷨���յõ�һ�����·������һ���ڵ㵽�������нڵ�����·���������㷨������·���㷨������Ϊ����ͼ�㷨��һ����ģ�顣��Ҫ�ص�������ʼ��Ϊ������������չ��ֱ����չ���յ�Ϊֹ��

�㷨˼�룺

> ������G=(V,E)��һ����Ȩ����ͼ����ͼ�ж��㼯��V�ֳ����飬��һ��Ϊ��������·���Ķ��㼯�ϣ���S��ʾ����ʼʱS��ֻ��һ��Դ�㣬�Ժ�ÿ���һ�����·�� , �ͽ����뵽����S�У�ֱ��ȫ�����㶼���뵽S�У��㷨�ͽ����ˣ�
> 
> �����ڶ���Ϊ����δȷ�����·���Ķ��㼯�ϣ���U��ʾ���������·�����ȵĵ����������ΰѵڶ���Ķ������S�С��ڼ���Ĺ����У��ܱ��ִ�Դ��v��S�и���������·�����Ȳ����ڴ�Դ��v��U���κζ�������·�����ȡ����⣬ÿ�������Ӧһ�����룬S�еĶ���ľ�����Ǵ�v���˶�������·�����ȣ�U�еĶ���ľ��룬�Ǵ�v���˶���ֻ����S�еĶ���Ϊ�м䶥��ĵ�ǰ���·�����ȡ�


�㷨���裺

a.����ʼʱ��Sֻ����Դ�㣬��S��{v}��v�ľ���Ϊ0��U������v����������㣬��:U={���ඥ��}����v��U�ж���u�бߣ���u,v��������Ȩֵ����u����v�ĳ����ڽӵ㣬��u,v��ȨֵΪ�ޡ�

b.����U��ѡȡһ������v��С�Ķ���k����k������S�У���ѡ���ľ������v��k�����·�����ȣ���

c.����kΪ�¿��ǵ��м�㣬�޸�U�и�����ľ��룻����Դ��v������u�ľ��루��������k����ԭ�����루����������k���̣����޸Ķ���u�ľ���ֵ���޸ĺ�ľ���ֵ�Ķ���k�ľ�����ϱ��ϵ�Ȩ��

d.���ظ�����b��cֱ�����ж��㶼������S�С�

����![����дͼƬ����](http://img.blog.csdn.net/20160613154953498)��

����Dijkstra�㷨��ʾ


##��.��Dijkstra�㷨��Javaʵ�֣�

  

```
public class Dijkstra {
	 private static int M = 10000; //��·��ͨ
	 public static void main(String[] args) {
	//�ڽӾ��� 
	    int[][] weight = { 
	        {0,10,M,30,100}, 
	        {M,0,50,M,M}, 
	        {M,M,0,M,10}, 
	        {M,M,20,0,60}, 
	        {M,M,M,M,0} 
	    };
	     
	    int start=0; 
	    int[] shortPath = dijkstra(weight,start); 
	      
	    for(int i = 0;i < shortPath.length;i++) 
	       System.out.println("��"+start+"������"+i+"����̾���Ϊ��"+shortPath[i]); 
	 }
	  
	 public static int[] dijkstra(int[][] weight, int start) {
	 //����һ������ͼ��Ȩ�ؾ��󣬺�һ�������start����0��ţ�������������У� 
	 //����һ��int[] ���飬��ʾ��start���������·������ 
	 int n = weight.length;      //�������
	 int[] shortPath = new int[n];  //����start��������������·��
	 String[] path = new String[n];  //����start�������������·�����ַ�����ʾ
	 for(int i=0;i<n;i++) 
	       path[i]=new String(start+"-->"+i); 
	 int[] visited = new int[n];   //��ǵ�ǰ�ö�������·���Ƿ��Ѿ����,1��ʾ����� 
	  
	 //��ʼ������һ�������Ѿ����
	 shortPath[start] = 0;
	 visited[start] = 1;
	  
	 for(int count = 1; count < n; count++) {   //Ҫ����n-1������
	  int k = -1;        //ѡ��һ�������ʼ����start�����δ��Ƕ��� 
	  int dmin = Integer.MAX_VALUE;
	  for(int i = 0; i < n; i++) {
	  if(visited[i] == 0 && weight[start][i] < dmin) {
	   dmin = weight[start][i];
	   k = i;
	  }
	  }
	   
	  //����ѡ���Ķ�����Ϊ��������·�����ҵ�start�����·������dmin 
	  shortPath[k] = dmin;
	  visited[k] = 1;
	   
	  //��kΪ�м�㣬������start��δ���ʸ���ľ��� 
	  for(int i = 0; i < n; i++) {
	  if(visited[i] == 0 && weight[start][k] + weight[k][i] < weight[start][i]) {
	   weight[start][i] = weight[start][k] + weight[k][i];
	   path[i] = path[k] + "-->" + i; 
	  }
	  }
	 }
	 for(int i = 0; i < n; i++) {
	  System.out.println("��"+start+"������"+i+"�����·��Ϊ��"+path[i]);
	 }
	 System.out.println("====================================="); 
	 return shortPath;
	 }
	}
```

���н����

```
��0������0�����·��Ϊ��0-->0
��0������1�����·��Ϊ��0-->1
��0������2�����·��Ϊ��0-->3-->2
��0������3�����·��Ϊ��0-->3
��0������4�����·��Ϊ��0-->3-->2-->4
=====================================
��0������0����̾���Ϊ��0
��0������1����̾���Ϊ��10
��0������2����̾���Ϊ��50
��0������3����̾���Ϊ��30
��0������4����̾���Ϊ��60
```