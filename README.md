#include <iostream>
using namespace std;

// Function to maintain the max heap property
void Maxheap(int Arr[], int n, int i) {
    int largest = i;
    int l = 2 * i + 1; // left child index
    int r = 2 * i + 2; // right child index

    // If left child is larger than root
    if (l < n && Arr[l] > Arr[largest]) {
        largest = l;
    }
    // If right child is larger than largest so far
    if (r < n && Arr[r] > Arr[largest]) {
        largest = r;
    }
    // If largest is not root
    if (largest != i) {
        swap(Arr[i], Arr[largest]); // Swap the root with the largest
        Maxheap(Arr, n, largest);    // Recursively heapify the affected sub-tree
    }
}

// Function to perform heapsort
void Maxheapsort(int Arr[], int n) {
    // Build max heap
    for (int i = n / 2 - 1; i >= 0; i--) { // Start from the last non-leaf node
        Maxheap(Arr, n, i);
    }
    // One by one extract elements from the heap
    for (int i = n - 1; i > 0; i--) {
        swap(Arr[0], Arr[i]); // Move current root to end
        Maxheap(Arr, i, 0);    // Call max heap on the reduced heap
    }
}

// Function to display the array
void Display(int Arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << Arr[i] << " ";
    }
    cout << "\n";
}

int main() {
    int n;
    cout << "How many elements do you want to sort: ";
    cin >> n;
    
    int Arr[n]; // Declare the array after reading n

    cout << "Enter " << n << " elements: ";
    for (int i = 0; i < n; i++) {
        cin >> Arr[i];
    }
    
    Maxheapsort(Arr, n);
    cout << "This is the sorted array:\n";
    Display(Arr, n);
    
    return 0; 
}
      
