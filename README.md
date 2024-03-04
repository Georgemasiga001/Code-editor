 
#include <iostream>

// Stack using Array
class StackArray {
private:
    static const int MAX_SIZE = 100;
    int arr[MAX_SIZE];
    int top;

public:
    StackArray() : top(-1) {}

    bool isEmpty() {
        return top == -1;
    }

    bool isFull() {
        return top == MAX_SIZE - 1;
    }

    void push(int value) {
        if (!isFull()) {
            arr[++top] = value;
            std::cout << "Pushed " << value << " to stack (Array)\n";
        } else {
            std::cout << "Stack overflow (Array)\n";
        }
    }

    void pop() {
        if (!isEmpty()) {
            std::cout << "Popped " << arr[top--] << " from stack (Array)\n";
        } else {
            std::cout << "Stack underflow (Array)\n";
        }
    }
};

// Node for Linked List
struct Node {
    int data;
    Node* next;

    Node(int value) : data(value), next(nullptr) {}
};

// Stack using Linked List
class StackLinkedList {
private:
    Node* top;

public:
    StackLinkedList() : top(nullptr) {}

    bool isEmpty() {
        return top == nullptr;
    }

    void push(int value) {
        Node* newNode = new Node(value);
        newNode->next = top;
        top = newNode;
        std::cout << "Pushed " << value << " to stack (Linked List)\n";
    }

    void pop() {
        if (!isEmpty()) {
            Node* temp = top;
            std::cout << "Popped " << temp->data << " from stack (Linked List)\n";
            top = top->next;
            delete temp;
        } else {
            std::cout << "Stack underflow (Linked List)\n";
        }
    }
};

int main() {
    StackArray stackArray;
    StackLinkedList stackLinkedList;

    stackArray.push(10);
    stackArray.push(20);
    stackArray.pop();

    stackLinkedList.push(30);
    stackLinkedList.push(40);
    stackLinkedList.pop();

    return 0;
