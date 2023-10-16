# test_10_16
#include <stdio.h>

typedef struct ThreadNode{
	int data;
	struct ThreadNode *lchild,*rchild;
	int ltag,rtag;
}ThreadNode,*ThreadTree;
//线索二叉树找后继
ThreadNode* FirstNode(ThreadNode* p){
	if(p->ltag == 0)
		p = p->lchild;
	return p;
}
ThreadNode *NextNode(ThreadNode* p){
	if(p->rtag == 0)
		return FirstNode(p->rchild);
	else
		return p->rchild;
}
//中序线索二叉树进行中序遍历
void InOrder(ThreadNode* T){
	for(ThreadNode* p = FirstNode(T);p != NULL;p = NextNode(T));
	visit(p);
}
//线索二叉树找前驱
ThreadNode* LastNode(ThreadNode* p){
	if(p->rtag == 0)
		p = p->rchild;
	return p;
}
ThreadNode *PreNode(ThreadNode* p){
	if(p->ltag == 0)
		return LastNode(p->lchild);
	else
		return p->lchild;
}
void InOrder(ThreadNode* T){
	for(ThreadNode* p = LastNode(T);p != NULL;p = PreNode(p));
	visit(p);
}
//树的存储结构
//双亲表示法
#define Max_Tree_Size 100
typedef struct{
	int data;
	int parent;
}PTNode;
typedef struct{
	PTNode nodes[Max_Tree_Size];
	int n;
}PTree;
//孩子表示法
struct CTNode{
	int child;
	struct CTNode* next;
};
typedef struct{
	int data;
	struct CTNode* firstchild;
}CTBox;
typedef struct{
	CTBox nodes[Max_Tree_Size];
	int n,r;
}CTree;
//孩子兄弟表示法
typedef struct CSNode{
	int data;
	struct CSNode *firstchild,*nextsibling;
}CSNode,*CSTree;
