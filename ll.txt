package LinkedList;
class SLL{ //user defined data sturcture
         Node head;
         Node tail;
         int size;
         void InsertAtEnd(int val){
             Node temp=new Node(val);
             if(head==null) head=tail=temp;
             else{
                 tail.next=temp;
                 tail=temp;
             }
             size++;
         }
    void InsertAtHead(int val){
        Node temp=new Node(val);
        if(head==null) head=tail=temp;
        else{
           temp.next=head;
           head=temp;
        }
        size++;
    }
    void insert(int idx,int val){
        if(idx==0) {
            InsertAtHead(val);
            return;
        }
        if(idx==size){
            InsertAtEnd(val);
            return;
        }
        if(idx>size|| idx<0){
            System.out.println("invalid index");
            return;
        }
        Node temp=new Node(val);
        Node x=head;
        for (int i = 1; i <=idx-1 ; i++) {
            x=x.next;
        }
        //insertion
        temp.next=x.next;
        x.next=temp;
        size++;
    }
    void set(int idx , int val){
        if(idx==size-1) {
            tail.val=val;
        }
        if(idx>=size || idx<0){
            throw new Error("Invalid Index");
        }
        Node temp= head;
        for (int i = 1; i <idx ; i++) {
            temp=temp.next;
        }
        temp.val=val;
    }
    int get(int idx) throws Error{
             if(idx==size-1) return tail.val;
             if(idx>=size || idx<0){
                 throw new Error("Invalid Index");
             }
             Node temp= head;
        for (int i = 1; i <idx ; i++) {
           temp=temp.next;
        }
        return temp.val;
    }
    void print(){
             Node temp=head;
             while(temp!=null){
                 System.out.print(temp.val+" ");
                 temp=temp.next;
             }
             System.out.println();
         }
    void deleteAtHead() throws Error{
             if(head==null) throw new Error("list is empty");
             head=head.next;
             size--;
    }
    void delete(int idx) throws Error{
         if(idx==0){
             deleteAtHead();
             return;
         }
        if(head==null) throw new Error("list is empty");
        if(idx<0 || idx>=size) throw new Error("Invalid Index");
        Node temp=head;
        for (int i = 1; i < idx; i++) {
            temp=temp.next;
        }
        if(temp.next==tail){
            tail=temp;
        }
        temp.next=temp.next.next;
        size--;
    }
}
public class implementationLL {
    public static void main(String[] args) {
       SLL list =new SLL();
       list.InsertAtEnd(10);
       list.InsertAtEnd(120);
       list.InsertAtHead(20);
       list.insert(2,100);
       list.print();
       list.set(2,90);
       list.print();
    }
}
