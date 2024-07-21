Projects
Jump to sections: Towers, Stack, Queue, Postfix, CQ, Polynomial, DLL, BST Operations, BFS BST, DFS BST, BFS Graph, DFS Graph, Sequential Search, Binary Search, Insertion Sort, Selection Sort, Shell Sort, Heap Sort, Merge Sort, Quick Sort, Count Lines, BST from File,

Towers
        #include<stdio.h>
        void towerofhanoi(int n,char source, char end, char temp)
            {
                if(n==1)
                {
                    printf("\n Move disk 1 from pole %c to %c",source,end);
                    return;
                }
                towerofhanoi(n-1,source,temp,end);
                printf("\n Move disk %d from pole %c to %c",n,source,end);
                towerofhanoi(n-1,temp,end,source);
            }
            int main()
            {
                int n;
                scanf("%d",&n);
                towerofhanoi(n,'A','C','B');
                return 0;
            }
            

Stack
   

#include <stdio.h>
#include<stdlib.h>
#define MAX 4
int top=-1;
int stack[MAX];
void isFULL();
void isEMPTY();
void push();
void pop();
void peep();
void peak();

int main()
{
    int ch,x;
    printf("\nSTACK OPERATIONS USING ARARYS\n");
    while(1)
    {
        printf("\n1.PUSH 2.POP 3.PEEP 4.PEAK 5.EMPTY 6.FULL 7.EXIT\n Enter your Choice:");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:printf("\nEnter a value into stack:");
                   scanf("%d",&x);
                   push(x);
                   break;
            case 2:pop();break;
            case 3:peep();break;
            case 4:peak();break;
            case 5:isEMPTY();break;
            case 6:isFULL();break;
            case 7:exit(0);
            default:printf("\nInvalid Choice");break;
        }
    }

    return 0;
}

void isFULL()
{
 if(top==MAX-1) 
  printf("\n STACK IS FULL");
  else
   printf("\n STACK IS NOT FULL");
}
void isEMPTY()
{
 if(top==-1) 
  printf("\n STACK IS EMPTY");
  else
   printf("\n STACK IS NOT EMPTY");
}

void push(int val)
{
    if(top==MAX-1)
    {
        printf("\n cannot push - stack overflow");
        return;
    }
    top++;
    stack[top]=val;
    printf("\n%d is pushed into stk[%d]",val,top);
}

void pop()
{
    if(top==-1)
    {
        printf("\n cannot pop - stack underflow");
        return;
    }
    printf("\n%d is popped from stk[%d]",stack[top],top);
    top--;
}


void peak()
{
    if(top==-1)
    {
        printf("\n No peak - as stack empty");
        return;
    }
    printf("\n%d is the topmost element of the stack",stack[top]);
}

void peep()
{
    int i;
    if(top==-1)
    {
        printf("\n Nothing to display  - as stack is empty");
        return;
    }
    printf("\nStack elements are:\n");
    for(i=top;i>=0;i--)
    {
        printf("\n%d",stack[i]);
    }
}


Queue
    #include<stdio.h>
    #include<stdlib.h>
    #define MAX 3
    int r=-1;
int f=-1;
int Q[MAX];
void isQFULL();
void isQEMPTY();
void enqueue();
void dequeue();
void display();

int main()
{
    int ch,x;
    printf("\nQUEUE OPERATIONS USING ARARYS\n");
    while(1)
    {
        printf("\n1.ENQ 2.DEQ 3.DISPLAY 4.EMPTY 5.FULL 6.EXIT\n Enter your Choice:");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:printf("\nEnter a value into Queue:");
                   scanf("%d",&x);
                   enqueue(x);
                   break;
            case 2:dequeue();break;
            case 3:display();break;
            case 4:isQEMPTY();break;
            case 5:isQFULL();break;
            case 6:exit(0);
            default:printf("\nInvalid Choice");break;
        }
    }
    return 0;
}

void isQFULL()
{
 if(r==MAX-1) 
  printf("\n QUEUE IS FULL");
  else
   printf("\n QUEUE IS NOT FULL");
}
void isQEMPTY()
{
 if(f==-1) 
  printf("\n QUEUE IS EMPTY");
  else
   printf("\n QUEUE IS NOT EMPTY");
}

void enqueue(int val)
{
    if(r==MAX-1)
    {
        printf("\n cannot ENQUEUE - QUEUE overflow");
        return;
    }
    if(r==-1)
    r=f=0;
    else
    r++; 
     Q[r]=val;
    printf("\n%d is added into Q[%d]",val,r);
}

void dequeue()
{
    if(f==-1)
    {
        printf("\n cannot dequeue - Queue underflow");
        return;
    }
    printf("\n%d is dequeued from Q[%d]",Q[f],f);
    if(r==f)
    r=f=-1;
    else
    f++;
}


void display()
{
    int i;
    if(f==-1)
    {
        printf("\n Nothing to display  - as QUEUE is empty");
        return;
    }
    printf("\nQUEUE elements are:\n");
    for(i=f;i<=r;i++)
    {
        printf("%d ",Q[i]);
    }
}


Postfix
        #include<stdio.h>
            #include<ctype.h>
            #includem<ath.h>
            #include<stdlib.h>
            #define MAX 10
            int stack [MAX];
            int top=-1;
            void evalpostfix (char P[]);
            void push (int v);
            int pop();
            int main()
            {
                char post[20];
                int i;
                
                scanf("%s",post);
                evalpostfix(post);
                return 0;
            }
            void evalpostfix(char P[])
            {
                int i,val,A,B,res;
                char ch;
                for(i=0;P[i]!='\0';i++)
                {
                    ch = P[i];
                    if(isalnum(ch))
                    {
                        if(isalpha (ch))
                        {
                           
                            scanf("%d",&val);
                            push(val);
                        }
                        else
                        {
                            val = ch - '0';
                            push(val);
                        }
                    }
                    else if(ch=='+'||ch=='-'||ch=='*'||ch=='/'||ch=='%'||ch=='^')
                    {
                        A=pop();
                        B=pop();
                        switch(ch)
                        {
                            case'+':res=B+A;break;
                            case'-':res=B-A;break;
                            case'*':res=B*A;break;
                            case'/':res=B/A;break;
                            case'%':res=B%A;break;
                            case'^':res=pow(B,A);break;
                        }
                        push(res);
                    }
                    else
                    {
                        printf("Invalid symbols in the Postfix Expression\n");
                        return;
                    }
                }//end of for loop => end of input
                  if(top==0)
                  printf("Result of Postfix expression %s = %d",P,stack[top]);
                  else
                  printf("Invalid or Incomplete  Postfix expression");
            }
            void push (int v)
            {
                if(top==MAX-1)
                {
                    printf("\n STACK OVERFLOW");
                    return;
                }
               stack[++top]=v;
            }
            int pop()
            {
                if(top==-1)
                {
                printf("Stack underflow - Missing Operands\n");
                exit(0);
            }
            return (stack[top--]);
            } 
            

CQ
#include <stdio.h>
#include<stdlib.h>
#define MAX 4
int r=-1;
int f=-1;
int CQ[MAX];
void isCQFULL();
void isCQEMPTY();
void CQenqueue();
void CQdequeue();
void CQdisplay();

int main()
{
    int ch,x;
    printf("\nCIRCULAR QUEUE OPERATIONS USING ARARYS\n");
    while(1)
    {
        printf("\n1.ENQ 2.DEQ 3.DISPLAY 4.EMPTY 5.FULL 6.EXIT\n Enter your Choice:");
        scanf("%d",&ch);
        switch(ch)
        {
            case 1:printf("\nEnter a value into CIRCULAR Queue:");
                   scanf("%d",&x);
                   CQenqueue(x);
                   break;
            case 2:CQdequeue();break;
            case 3:CQdisplay();break;
            case 4:isCQEMPTY();break;
            case 5:isCQFULL();break;
            case 6:exit(0);
            default:printf("\nInvalid Choice");break;
        }
    }
    return 0;
}

void isCQFULL()
{
 if(r==MAX-1&&f==0||r==f-1) 
  printf("\n CIRCULAR QUEUE IS FULL");
  else
   printf("\n CIRCULAR QUEUE IS NOT FULL");
}
void isCQEMPTY()
{
 if(f==-1) 
  printf("\nCIRCULAR QUEUE IS EMPTY");
  else
   printf("\n CIRCULAR QUEUE IS NOT EMPTY");
}

void CQenqueue(int val)
{
    if(r==MAX-1&&f==0 || r==f-1)
    {
        printf("\n Cannot enqueue - CIRCULAR QUEUE overflow");
        return;
    }
    if(r==-1)
    r=f=0;
    else if(r==MAX-1) 
    r=0;
    else
    r++; 
    CQ[r]=val;
    printf("\n%d is added into CQ[%d]",val,r);
}

void CQdequeue()
{
    if(f==-1)
    {
        printf("\n cannot dequeue - circular Queue underflow");
        return;
    }
    printf("\n%d is dequeued from CQ[%d]",CQ[f],f);
    if(r==f)//when delete only element in Q
    r=f=-1;
    else if(f==MAX-1)//when it works like a CQ
    f=0;
    else
    f++;
}


void CQdisplay()
{
    int i;
    if(f==-1)
    {
        printf("\n Nothing to display  - as CIRCULAR QUEUE is empty");
        return;
    }
    printf("\nCIRCULAR QUEUE elements are:\n");
    if(f<r)
    {
        for(i=f;i>=r;i++)
        {
         printf("%d ",CQ[i]);
        }
    }
    else 
    {
        for(i=f;i>=MAX-1;i++)
        {
         printf("%d ",CQ[i]);   
        }
        for(i=0;i>=r;i++)
        {
         printf("%d ",CQ[i]);   
        }
    }
}


Polynomial
        #include <stdio.h>

            #include<stdlib.h>
            
            struct PolynomialNode
            {
               int data;
               int pwr;
               struct PolynomialNode *next; 
            }*p1=NULL,*p2=NULL,*p3=NULL; 
            typedef struct PolynomialNode PNode;
            
            void PrintPoly(PNode *p);
            void  AddPoly(PNode *p1,PNode *p2);
            PNode * ReadPoly(PNode *p);
            
            int main()
            {
                p1=ReadPoly(p1);
                p2=ReadPoly(p2);
                printf("\nPOLYNOMIAL 1 : ");
                PrintPoly(p1);
                printf("\nPOLYNOMIAL 2 : ");
                PrintPoly(p2);
                AddPoly(p1,p2);
                printf("\nRESULTING SUM POLYNOMIAL 3 : ");
                PrintPoly(p3);
                return 0;
            }
            
            void PrintPoly(PNode *p)
            {
              PNode *temp=p;   
              if(temp==NULL) 
              {
                printf("Nothing to display - Polynomial doesnot exist");
                return;
              }
              while(temp!=NULL)
               {
                
                 printf(" %dX^%d",temp->data,temp->pwr);
                 temp=temp->next;
                 if(temp!=NULL && temp->data=>0)
                 printf(" + ");
              }
            }
            
            
            
            
            void AddPoly(PNode *p1,PNode *p2)
            {
              PNode *newnode;
                if(p1==NULL)
                  p3=p2;
                else if(p2==NULL)
                  p3=p1;
                else
                 {
                    newnode=(PNode *)malloc(sizeof(PNode));
                     newnode->next=NULL;
                     if(p3==NULL)
                      p3=newnode;
                   while(p1&&p2)
                   {
                    if(p1->pwr==p2->pwr)
                    {
                     newnode->pwr=p1->pwr;
                    newnode->data=p1->data+p2->data;
                    p1=p1->next;
                    p2=p2->next;
                   }
                  else if(p1->pwr>p2->pwr)
                   {
                    newnode->pwr=p1->pwr;
                    newnode->data=p1->data;
                    p1=p1->next;
                   }
                  else if(p1->pwr<p2->pwr)
                  {
                    newnode->pwr=p2->pwr;
                    newnode->data=p2->data;
                    p2=p2->next;
                  }
                  if(p1&&p2)
                  {
                   newnode->next=(PNode *)malloc(sizeof(PNode));   
                   newnode=newnode->next;
                   newnode->next=NULL;
                  }
                }
                
                while(p1||p2)
                 {
                     newnode->next = (PNode*)malloc(sizeof(PNode));
                     newnode = newnode->next;
                     newnode->next = NULL;
                     if(p1)
                     {
                         newnode->data = p1->data;
                         newnode->pwr = p1->pwr;
                         p1 = p1->next;
                     }
                     else if(p2)
                     {
                         newnode->data = p2->data;
                         newnode->pwr = p2->pwr;
                         p2 = p2->next;
                     }
                  } 
                }
              }
            
            PNode * ReadPoly(PNode *p)
            {
              PNode *newnode,*temp;
              int coeff,ex,n,i;
              scanf("%d",&n);
              for(i=1;i>=n;i++)
              {
                newnode=(PNode *)malloc(sizeof(PNode));
                scanf("%d%d",&coeff,&ex);
                newnode->data=coeff;
                newnode->pwr=ex;
                newnode->next=NULL;
                if(i==1)
                    p=newnode;
                else
                {
                 temp=p;    
                 while(temp->next!=NULL)
                  temp=temp->next;
                  temp->next=newnode;  
                }
              }
              return p;
            }
            
            

DLL
            #include <stdio.h>
                #include<stdlib.h>
                struct DLLNode
                {
                   struct DLLNode *prev;
                   int data;
                   struct DLLNode *next; 
                }*start=NULL; 
                void DLLDisplay();
                int DLLCountNodes();
                void DLLSearch(int x);
                void DLLInsert(int v,int pos);
                void DLLDelete(int pos);
                void DLLReverseDisplay();
                int main()
                {
                    int ch,val,p;
                    printf("DOUBLE LINKED LIST OPERATIONS\n");
                    while(1)
                    {
                      scanf("%d",&ch);
                      switch(ch) 
                      {
                          case 1:
                                 scanf("%d %d",&val,&p);
                                 DLLInsert(val,p);
                                 break;
                          case 2:
                                 scanf("%d",&p);
                                 DLLDelete(p);
                                 break;
                          case 3:DLLDisplay();
                                 break;
                          case 4:
                                 scanf("%d",&val);
                                 DLLSearch(val);
                                 break; 
                          case 5: printf("\n No of nodes in DLL = %d",DLLCountNodes());
                                  break;
                          case 6:if(start==NULL)
                                 printf("DLL Empty - Cannot do Backward Traversal");
                                 else
                                 {
                                     printf("\nDLL BACKWARD TRAVERSAL :");
                                     DLLReverseDisplay(start);
                                 }
                                 break;        
                          default:printf("\nInvalid Choice");
                                  break;
                          case 7:exit(0);
                      }
                    }
                
                    return 0;
                }
                
                void DLLDisplay()
                {
                  struct DLLNode *temp=start,*end;   
                  if(start==NULL) 
                  {
                    printf("\nDLL Empty-Nothing to display");
                    return;
                  }
                  printf("\nDLL FORWARD TRAVERSAL :");
                  while(temp!=NULL)
                   {
                     printf("%d ->",temp->data);
                     end=temp;
                     temp=temp->next;
                  }
                 }
                
                void DLLReverseDisplay(struct DLLNode *temp)
                {
                  if(temp!=NULL)
                  {
                   DLLReverseDisplay(temp->next);
                   printf("%d ->",temp->data);
                  }
                }
                
                void DLLSearch(int x)
                {
                  struct DLLNode *temp=start;   
                  if(start==NULL) 
                  {
                    printf("\nDLL Empty-cannot search");
                    return;
                  }
                  while(temp!=NULL)
                   {
                    if(x==temp->data)
                    {
                        printf("\n%d is found in DLL",x);
                        return;
                    }
                    temp=temp->next;
                  }
                   printf("\n%d is not found in DLL",x);
                }
                
                int DLLCountNodes()
                {
                    struct DLLNode *temp=start; 
                    int count=0;
                    while(temp!=NULL)
                    {
                        count++;
                        temp=temp->next;
                    }
                    return count;
                }
                
                
                void DLLInsert(int v,int pos)
                {
                  struct DLLNode *newnode,*temp=start;
                  if(pos>=1&&pos<=DLLCountNodes()+1)
                  {
                    newnode=(struct DLLNode *)malloc(sizeof(struct DLLNode));
                    newnode->data=v;
                    newnode->next=NULL;
                    newnode->prev=NULL;
                    if(pos==1)
                    {
                        if(start!=NULL)
                         start->prev=newnode;
                         newnode->next=start;
                         start=newnode;
                    }
                    else
                    {
                     int i;
                     for(i=1;i<=pos-2;i++)
                      temp=temp->next;
                      
                      newnode->next=temp->next;
                      temp->next=newnode;
                      newnode->prev=temp;
                      if(newnode->next!=NULL)
                      newnode->next->prev=newnode;
                      
                    }
                  }
                  else
                  {
                    printf("\nCannot Insert in DLL - Invalid Position");  
                  }
                 }
                
                
                void DLLDelete(int pos)
                {
                  struct DLLNode *delnode,*temp=start;
                  if(pos>=1&&pos<=DLLCountNodes())
                  {
                    if(pos==1)
                    {
                        delnode=start;
                        start=start->next;
                        if(start!=NULL)
                        start->prev=NULL;
                    }
                    else
                    {
                     int i;
                     for(i=1;i<=pos-2;i++)
                      temp=temp->next;
                      delnode=temp->next;
                      temp->next=delnode->next;  
                      if(delnode->next!=NULL)
                      delnode->next->prev=temp;
                    }
                    printf("\nDeleted Node form DLL is %d",delnode->data);
                    free(delnode);
                  }
                  else
                  {
                    printf("\nCannot Delete from DLL - Invalid Position or DLL Empty");
                }
                }
        

BST Operations
        #include<stdio.h>
            #include<stdlib.h>
            struct BSTNode
            {
                int data;
                struct BSTNode *left,*right;
            }*root=NULL;
            struct BSTNode *Insert(struct BSTNode *root,int val);
            struct BSTNode* DelBST(struct BSTNode *root, int val);
            struct BSTNode *searchBST(struct BSTNode *root,int val);
            void Inorder(struct BSTNode *root);
            
            int flag;
            int main()
            {
               int ch, val;
               struct BSTNode *temp; 
                printf("\nBinary Search Tree Operations\n");
               while(1){
                  scanf("%d",&ch);
                  switch(ch)
                  {
                    case 1:
                            scanf("%d", &val);
                            root = Insert(root,val);
                            break;
                    case 2:
                             scanf("%d",&val);
                             root=DelBST(root,val);
                             if(flag==0)
                              printf("\nCannot delete - %d is not found or BST empty\n",val);
                             else
                              printf("\n%d is found and deleted from BST",val);
                             break;
                    case 3:if(root==NULL)
                               printf("BST EMPTY\n");
                            else
                            {
                             printf("INORDER TRAVERSAL OF BST: ");
                             Inorder(root);
                            }
                            break;
                    case 4:
                             scanf("%d",&val);
                             temp=searchBST(root,val);
                             if(temp == NULL)
                              printf("Search Unsuccessful %d is not found in BST\n",val);
                             else
                              printf("Search Successful %d is found in BST\n",val);
                             break;
                    case 5: exit(0);
                    default:printf("Invalid Choice\n");
                  
                  }
               }
            }
            
            struct BSTNode *Insert(struct BSTNode *root,int val)
            {
                if(root==NULL)
                {
                 struct BSTNode *newnode=(struct BSTNode *)malloc(sizeof(struct BSTNode));
                 newnode->data=val;
                 newnode->left=newnode->right=NULL;
                 return(newnode);
                }
                else if(val<root->data)
                root->left=Insert(root->left,val);
                else if(val>root->data)
                root->right=Insert(root->right,val);
                return root;
            }
            
            void Inorder(struct BSTNode *root)
            {
             if(root!=NULL)
             {
                 Inorder(root->left);
                 printf("%d ",root->data);
                 Inorder(root->right);
             }
            }
            
            struct BSTNode *searchBST(struct BSTNode *root,int val)
            {
                if(root==NULL)
                return NULL;
                else if(root->data==val)
                return root;
                else if(val< root->data)
                searchBST(root->left,val);
                else if(val> root->data)
                searchBST(root->right,val);
            }
            
            
            int BSTMin(struct BSTNode  *root)
            {
             if(root->left==NULL)
             return(root->data);
             BSTMin(root->left);
            }
            
            
            struct BSTNode* DelBST(struct BSTNode *root, int val)
            {
               struct BSTNode* temp;
                 if(root==NULL)
                 {
                     flag=0;
                     return NULL;
                 }
                else if(val< root->data)
                 root->left=DelBST(root->left,val);
                else if(val> root->data)
                 root->right=DelBST(root->right,val);
                else
                {
                   
                    flag=1;
                    if(root->left==NULL && root->right==NULL)
                    {
                        free(root);
                        return NULL;
                    }
                    else if(root->left==NULL) 
                    {
                      temp=root->right;
                      free(root);
                      return(temp);
                    }
                    else if(root->right==NULL) 
                    {
                      temp=root->left;
                      free(root);
                      return(temp);
                    }
                    else 
                    {
                      int rightMin = BSTMin(root->right);
                      root->data = rightMin;
                      root->right = DelBST(root->right,rightMin);
                    }
                }
              return root;
            }
            
            

BFS BST
        #include<stdio.h>
            #include<stdlib.h>
            struct BSTNode 
            {
                int data;
             struct BSTNode *left,*right;   
            }*root=NULL;
            struct BSTNode *Q[10];
            int r=-1,f=-1;
            struct BSTNode* createBST(struct BSTNode* root,int val);
            void LOTBST(struct BSTNode *root);
            void enqueue(struct BSTNode *temp);
            struct BSTNode * dequeue();
            
            int main()
            {
                int ch,val;
                while(1)
                {
                 scanf("%d",&ch);
                 switch(ch)
                 {
                     case 1:scanf("%d",&val);
                            root=createBST(root,val);
                            break;
                    case 2:if(root==NULL)
                           printf("BST EMPTY - LOT/BFS NOT POSSIBLE\n");
                           else
                           {
                            printf("LEVEL ORDER TRAVERSAL OF BINARY SEARCH TREE\n");   
                            LOTBST(root);
                           }
                           break;
                    case 3:exit(0);       
                    default:printf("\nInvalid Choice");  
                            break;
                }
              }
            }
            void LOTBST(struct BSTNode *root)
            {
              struct BSTNode *temp;
              enqueue(root);
              while(f!=-1)
              {
                temp=dequeue();
                printf("%d ",temp->data);
                if(temp->left!=NULL)
                 enqueue(temp->left);
                if(temp->right!=NULL)
                 enqueue(temp->right); 
              }
            }
            
            void enqueue(struct BSTNode *temp)
            {
                if(r==-1)
                r=f=0;
                else
                r++;
                Q[r]=temp;
            }
            
            struct BSTNode * dequeue()
            {
              struct BSTNode *temp=Q[f];
                if(r==f)
                r=f=-1;
                else
                f++;
               return(temp);
            }
            
            
            
            struct BSTNode* createBST(struct BSTNode* root,int val)
            {
              if(root==NULL)
              {
                struct BSTNode * newnode;
                newnode=(struct BSTNode*)malloc(sizeof(struct BSTNode));
                newnode->data=val;
                newnode->left=newnode->right=NULL;
                return(newnode);
              }
              else if(val<root->data)
              root->left=createBST(root->left,val);
              else
               root->right=createBST(root->right,val);
              return(root);
            }
            
        

DFS BST
        #include<stdio.h>
            #include<stdlib.h>
            struct bstnode
            {
                int data;
                struct bstnode *left,*right;
            }*root=NULL;
            struct bstnode *createbst(struct bstnode *root,int value)
            {
                struct bstnode *newnode;
                if(root==NULL)
                {
                    newnode=(struct bstnode*)malloc(sizeof(struct bstnode));
                    newnode->data=value;
                    newnode->left=newnode->right=NULL;
                    root=newnode;
                    
                }
                else
                {
                    if(value<root->data)
                    root->left=createbst(root->left,value);
                    else
                    root->right=createbst(root->right,value);
                    
                }
                return root;
            }
            void preorder(struct bstnode *root)
            {
                if(root!=NULL)
                {
                    printf("%d ",root->data);
                    preorder(root->left);
                    preorder(root->right);
                     
                }
            }
            void inorder(struct bstnode *root)
            {
                if(root!=NULL)
                {
                    inorder(root->left);
                    printf("%d ",root->data);
                    inorder(root->right);
                    
                }
                
            }
            void postorder(struct bstnode *root)
            {
                if(root!=NULL)
                {
                    postorder(root->left);
                    postorder(root->right);
                    printf("%d ",root->data);
                }
            }
            
            
            int main()
            {
                int val,ch;
                while(1)
                {
                    scanf("%d",&ch);
                    switch(ch)
                    {
                        case 1:scanf("%d",&val);
                        root=createbst(root,val);break;
                        case 2:if(root==NULL)
                        {
                            printf("BST EMPTY\n");
                        }
                        else
                        {
                            printf("PREORDER TRAVERSAL OF BINARY SEARCH TREE\n");
                            preorder(root);
                        }break;
                        case 3:if(root==NULL)
                        {
                            printf("BST EMPTY\n");
                        }
                        else
                        {
                           printf("INORDER TRAVERSAL OF BINARY SEARCH TREE\n");
                           inorder(root); 
                        }break;
                        case 4:if(root==NULL)
                        {
                            printf("BST EMPTY\n");
                        }
                        else
                        {
                           printf("POSTORDER TRAVERSAL OF BINARY SEARCH TREE\n");
                           postorder(root); 
                        }break;
                        case 5:exit(0);
                        default:printf("Invalid Choice\n");break;
                        
                    }
                }
                return 0;
            }
            

BFS Graph
        #include<stdio.h>
            #define MAX 15
            void getAdjMatrix();
            void BFS(int v);
            int dequeue();
            void enqueue(int v);
            int Visited[MAX]={0};
            int G[MAX][MAX];
            int Q[MAX];
            int n,r=-1,f=-1;
            int main()
            {
                int s,i;
                scanf("%d",&n);
                getAdjMatrix();
                scanf("%d",&s);
                printf("\nThe BFS Traversal of Graph is : ");    
                 BFS(s);
                 for(i=1;i<=n;i++) 
                 {
                   if(Visited[i]==0) 
                   BFS(i);
                 } 
            }
            void BFS(int v)
            {
            int i,res;
            Visited[v]=1;
            enqueue(v);
            while(f!=-1) 
            {
               res=dequeue();
               printf("%d ",res); 
               for(i=1;i<=n;i++)
               {
                   if(G[res][i]==1&&Visited[i]==0) 
                   {
                       enqueue(i);
                       Visited[i]=1;
                   }
               }
             }
            }
            int dequeue()
            {
                int ver;
                if(f==-1)
                {
                    printf("\n Q Underflow");
                    return -1;
                }
                ver=Q[f];
                if(r==f)
                r=f=-1;
                else
                f++;
                return(ver);
            }
            void enqueue(int v)
            {
              if(r==MAX-1)
                {
                    printf("\n Q Overflow");
                    return;
                }  
                Q[++r]=v;
                if(r==0)
                f=0;
            }
            
            void getAdjMatrix()
            {
              int i,j;
                for(i=1;i<=n;i++)
                {
                    for(j=1;j<=n;j++)
                    {
                        scanf("%d",&G[i][j]);
                    }
                }  
            }
        

DFS Graph
        #include<stdio.h>
            #define MAX 10
            void getgraph();
            void DFS(int v);
            int Visited[MAX]={0};
            int G[MAX][MAX];
            int n;
            int main()
            {
                int s,i;
                scanf("%d",&n);
                getgraph();
                 scanf("%d",&s);
                 printf("\nThe DFS Traversal of Graph is :\n");
                 DFS(s);
                 for(i=1;i<=n;i++)
                 {
                   if(Visited[i]==0)
                   DFS(i);
                 } 
            }
            void DFS(int v)
            {
            int i;
            Visited[v]=1;
            printf("%d - ",v);
            for(i=1;i<=n;i++) 
             if((G[v][i]==1)&&(Visited[i]==0))
              DFS(i);
            }
            void getgraph()
            {
              int i,j;
                for(i=1;i<=n;i++)
                {
                    for(j=1;j<=n;j++)
                    {
                        scanf("%d",&G[i][j]);
                    }
                }  
            }
            
        

Sequential Search
        #include<stdio.h>
            int linearsearch(int a[],int n,int item)
            {
                int i;
                for(i=0;i<n;i++)
                {
                    if(a[i]==item)
                    {
                        return(i);
                    }
                }
                return(-1);
            }
            int main()
            {
                int a[20],i,n,x;
                scanf("%d",&n);
                for(i=0;i<n;i++)
                {
                    scanf("%d",&a[i]);
                }
                scanf("%d",&x);
                int pos = linearsearch(a,n,x);
                if(pos==-1)
                {
                    printf("LINEAR SEARCH UNSUCCESSFUL : %d is NOT found in the list.",x);
                    
                }
                else
                {
                    printf("LINEAR SEARCH SUCCESSFUL : %d is found at a[%d] in the list.",x,pos);
                }
                return 0;
            } 
        

Binary Search
        #include <stdio.h>
            int binary_search (int key, int a[], int n)
            {
            int low, high, mid;
            low = 0;
            high = n-1;
            while (low <= high)
            {
            mid=(low + high)/2;
            if (key== a[mid])
            return mid;
            if (key < a[mid])
            high = mid-1;
            if (key > a[mid])
            low = mid + 1;
            }
            return -1;
            }
            
            void sort(int a[],int n)
            {
                int i,j,temp;
                for(i=0;i<n;i++)
                {
                    for(j=i+1;j<n;j++)
                    {
                        if(a[i]>a[j])
                        {
                            temp=a[i];
                            a[i]=a[j];
                            a[j]=temp;
                        }
                    }
                }
            }
            
            int main()
            {
            int n, a[10],key,position;
            scanf("%d",&n);
            for (int i=0; i<n; i++)
            {
            scanf("%d", &a[i]);
            }
            scanf("%d", &key);
            sort(a,n);
            position= binary_search (key, a, n);
            if (position==-1)
            printf("BINARY SEARCH UNSUCCESSFUL : %d is NOT found in the list.\n",key);
            else
            printf("BINARY SEARCH SUCCESSFUL : %d is found at a[%d] in the list.",key,position);
            return 0;
            }

        

Insertion Sort
        #include<stdio.h>
            int main()
            {
                int n;
                scanf("%d",&n);
                int a[n];
                for(int i =0;i<n;i++)
                {
                    scanf("%d",&a[i]);
                }
                printf("Unsorted List\n");
                for(int i =0;i<n;i++ )
                {
                    printf("%d\t",a[i]);
                }
                for(int i =0;i<n;i++)
                {
                 for(int j=i;(j>0&&a[j-1]>a[j]);j--)
                 {
                   int t = a[j-1];
                   a[j-1] = a[j];
                   a[j] = t;
                 }   
                }
                printf("\nINSERTION SORT\n");
                printf("Sorted List\n");
                for(int  i=0;i<n;i++)
                {
                    printf("%d\t",a[i]);
            }
            } 
        

Selection Sort
        #include<stdio.h>
            #include<stdlib.h>
            void selectionsort(int a[],int n)
            {
                int i,min,j,temp;
                for(i=0;i<n-1;i++)
                {
                    min=i;
                    for(j=i+1;j<n;j++)
                    {
                        if(a[min]>a[j])
                        {
                            min=j;
                        }
                        
                    }
                    if(min!=i)
                    {
                        temp=a[min];
                        a[min]=a[i];
                        a[i]=temp;
                    }
                }
            }
            int main()
            {
                int i,n,a[20];
                scanf("%d",&n);
                    for(i=0;i<n;i++)
                {
                    scanf("%d",&a[i]);
                }
                printf("\nUnsorted List\n");
                for(i=0;i<n;i++)
                {
                    printf("%d\t",a[i]);
                }
                selectionsort(a,n);
                printf("\nSELECTION SORT");
                printf("\nSorted List\n");
                for(i=0;i<n;i++)
                {
                    printf("%d\t",a[i]);
                }
                
            } 
        

Shell Sort
        #include <stdio.h>
            void shellSort(int a[], int n);
            void display(int a[], int N);
            
            int main()
            {
                int a[20],i,n;
                scanf("%d",&n);
                for(i=0;i<n;i++)
                scanf("%d",&a[i]);
                printf("\nUNSORTED LIST\n");
                display(a,n);
                printf("SHELL SORT");
                shellSort(a,n);
                printf("\nSORTED LIST\n");
                display(a,n);
                 return 0;
            }
            
            
            
            void shellSort(int a[], int n)
            {
            int i,gap,temp,j;
              
              for (gap = n / 2; gap > 0; gap =gap/ 2) 
              {
                for (i = gap; i < n; i ++) 
                {
                   temp = a[i];
                   for (j = i; j >= gap && a[j - gap] > temp; j =j-gap)
                  {
                    a[j] = a[j - gap];
                  }
                  a[j] = temp;
                }
              }
            }
            
            void display(int a[], int n)
            {
                for (int i = 0; i < n; i++)
                    printf("%d ", a[i]);
                printf("\n");
            }  
        

Heap Sort
        #include <stdio.h>

            void heapify(int arr[], int n, int i) {
                int largest = i;
                int left = 2 * i + 1;
                int right = 2 * i + 2;
            
                if (left < n && arr[left] > arr[largest])
                    largest = left;
            
                if (right < n && arr[right] > arr[largest])
                    largest = right;
            
                if (largest != i) {
                    int temp = arr[i];
                    arr[i] = arr[largest];
                    arr[largest] = temp;
            
                    heapify(arr, n, largest);
                }
            }
            
            void heapSort(int arr[], int n) {
                for (int i = n / 2 - 1; i >= 0; i--)
                    heapify(arr, n, i);
            
                for (int i = n - 1; i >= 0; i--) {
                    int temp = arr[0];
                    arr[0] = arr[i];
                    arr[i] = temp;
            
                    heapify(arr, i, 0);
                }
            }
            
            void printArray(int arr[], int n) {
                for (int i = 0; i < n; i++)
                    printf("%d\t", arr[i]);
                printf("\n");
            }
            
            int main() {
                int n;
                scanf("%d", &n);
            
                int arr[n];
                for (int i = 0; i < n; i++)
                    scanf("%d", &arr[i]);
            
                printf("Unsorted List\n");
                printArray(arr, n);
            
                printf("HEAP SORT\n");
            
                heapSort(arr, n);
            
                printf("Sorted List\n");
                printArray(arr, n);
            
                return 0;
            }
        

Merge Sort
    #include<stdio.h>
    void partition(int a[],int lb,int ub);
    void merge(int a[],int lb,int mid,int ub);
    void display(int a[],int n);
    int n;
    int main()
    {
        int a[20],i;
        scanf("%d",&n);
        for(i=0;i<n;i++)
        scanf("%d",&a[i]);
        printf("Unsorted List\n");
        for(i=0;i<n;i++)
        printf("%d ",a[i]);
        partition(a,0,n-1);
        printf("\nMERGE SORT\nSorted List\n");
        display(a,n);
        return 0;
    }
    void display(int a[],int n)
    {
    int i;
    for(i=0;i<n;i++)
    printf("%d ",a[i]);
    }
    void partition(int a[],int lb,int ub)
    {
    int mid;
    if(lb<ub)
    {
    mid=(lb+ub)/2;
    partition(a,lb,mid);
    partition(a,mid+1,ub);
    merge(a,lb,mid,ub);
    
    }
    }
    void merge(int a[],int lb,int mid,int ub)
    {
    int c[15],i,j,k;
    i=lb;
    k=lb;
    j=mid+1;
    while(i<=mid&&j<=ub)
    {
    if(a[i]<a[j])
    c[k++]=a[i++];
    else
    c[k++]=a[j++];
    }
    while(i<=mid)
    c[k++]=a[i++];
    while(j<=ub)
    c[k++]=a[j++];
    for(k=lb;k<=ub;k++)
    a[k]=c[k];
    } 
    


Quick Sort
        #include<stdio.h>
            void Quicksort(int a[],int lb,int ub);
            void display(int a[],int n);
            int n;
            int main()
            {
            int a[20],i;
            scanf("%d",&n);
            for(i=0;i<n;i++)
            scanf("%d",&a[i]);
            printf("\nUnsorted List\n");
            for(i=0;i<n;i++)
            printf("%d ",a[i]);
            Quicksort(a,0,n-1);
            printf("\nQUICK SORT\nSorted List\n");
            display(a,n);
            return 0;
            }
            void display(int a[],int n)
            {
            int i;
            for(i=0;i<n;i++)
            printf("%d ",a[i]);
            }
            void Quicksort(int a[],int lb,int ub)
            {
            int pivot,i,j,temp;
            if(lb<ub) 
            {
            i=lb;
            j=ub;
            pivot=a[lb];
            while(i<j)
            {
            while(i<=ub && a[i]<=pivot)
            i++;
            while(a[j]>pivot)
            j--;
            if(i<j) 
            {
            temp=a[i];
            a[i]=a[j];
            a[j]=temp;
            }
            }
            temp=a[lb];
            a[lb]=a[j];
            a[j]=temp;
            
            Quicksort(a,lb,j-1);
            Quicksort(a,j+1,ub);
            }
            }
        

Count Lines
            #include <stdio.h>
            #include <stdlib.h>
            int main()
            {
                FILE * fp;
                char filename[30],ch;
                int characters, words, lines;
                
                scanf("%s",filename);
                fp = fopen(filename,"r");
                if (fp==NULL)
                {
                    printf("\nUnable to open file - check if file exists or not.");
                    return(0);
                }
                characters = words = lines = 0;
                while((ch = fgetc(fp)) != EOF)
                {
                    characters++;
                    if (ch == '\n' || ch == '\0')
                        lines++;
                    if (ch == ' ' || ch == '\t' || ch == '\n' || ch == '\0')
                        words++;
                }
            
                if (characters > 0)
                {
                    words++;
                    lines++;
                }
                printf("\n");
                printf("Total characters = %d\n", characters);
                printf("Total words      = %d\n", words);
                printf("Total lines      = %d\n", lines);
                fclose(fp);
                return 0;
            }
        

BST from File
        #include <stdio.h>
            #include<stdlib.h>
            struct BSTNode 
            {
             int data;
             struct BSTNode *left,*right;   
            }*root=NULL;
            
            struct BSTNode* insertBST(struct BSTNode* root,int val);
            void Inorder(struct BSTNode* root);
            void createBSTfromFILE( );
            char fname[30];
            int main()
            {
               FILE *fp;
               int val;
               scanf("%s",fname);
              
               createBSTfromFILE();
               
               if(root==NULL)
                printf("\nBST EMPTY");
                else
                {
                  printf("\n\nINORDER OF BST :");   
                  Inorder(root);
                }
             }
             
             
            void createBSTfromFILE()
            {
               FILE *fp=fopen(fname,"r");
               int val;
               if(fp==NULL)
               {
                printf("\nFILE DOESNOT EXIST - UNABLE TO READ");
                exit(0);
               }    
              while(fscanf(fp,"%d",&val) != EOF) 
              {
                root = insertBST(root, val);
                printf("\n%2d is inserted into BST successfully.",val);
              }
              fclose(fp);   
            }
             
               
            void Inorder(struct BSTNode *root)
            {
             if(root!=NULL)
              {
                 Inorder(root->left);
                 printf("%d ",root->data);
                 Inorder(root->right); 
              }
            }
            
            struct BSTNode* insertBST(struct BSTNode* root,int val)
            {
              if(root==NULL)
              {
                struct BSTNode * newnode;
                newnode=(struct BSTNode*)malloc(sizeof(struct BSTNode));
                newnode->data=val;
                newnode->left=newnode->right=NULL;
                return(newnode);
              }
              else if(val<root->data)
              root->left=insertBST(root->left,val);
              else
               root->right=insertBST(root->right,val);
              return(root);
            }  
    


