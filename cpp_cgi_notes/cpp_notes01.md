# Deep Copy of Objects in C++

The code below demonstrate it

```c++
/**
    * PtrMemberVar.hpp
 */
#pragma once

#include <iostream>
#include <stdexcept>

class PtrMemberVar
{
private:
    int maxSize; // store max size of p
    int length;  // store number of elements in p
    int *p;      // pointer at int array
public:
    // Constructor
    // Create an array of the size specified by the param size
    PtrMemberVar(int size);

    // copy constructor
    PtrMemberVar(const PtrMemberVar &otherObj);

    // function to insert num into the array at point p
    // If the index is out of bounds, the program is terminated
    // otherwise if it within bound or greater than the index of the last item, num is added at end
    void insertAt(int index, int num);

    // Function to output the data stored in the array p
    void print() const;

    // Destructor
    ~PtrMemberVar();
};

// Function to output the data stored in the array p
void PtrMemberVar::print() const
{
    for (int i = 0; i < length; i++)
    {
        std::cout << p[i] << " ";
    }
}

// function to insert num into the array at point p
// If the index is out of bounds, the program is terminated
// otherwise if it within bound or greater than the index of the last item, num is added at end
void PtrMemberVar::insertAt(int index, int num)
{

    // If index out of bound terminate the program
    // assert(index >= 0 && index < maxSize);
    if (index < length)
        p[index] = num;

    else
    {
        p[length] = num;
        length++;
    }
}

// Constructor
// Create an array of the size specified by the param size
PtrMemberVar::PtrMemberVar(int size = 10)
{
    if (size <= 0)
        maxSize = 10;
    else
        maxSize = size;

    length = 0;

    p = new int[maxSize];
}

// Destructor
PtrMemberVar::~PtrMemberVar()
{
    delete[] p;
}

PtrMemberVar::PtrMemberVar(const PtrMemberVar &otherObj)
{
    maxSize = otherObj.maxSize;
    length = otherObj.length;

    p = new int[maxSize];

    for (int i = 0; i < length; i++)
    {
        p[i] = otherObj.p[i];
    }
}

```

The next set of code calls and tests the Objects

```c++
void testCopyConst(PtrMemberVar temp)
{
    std::cout << "<===Inside 'testCopyConst'===>\n";
    std::cout << "Object temp data:";
    temp.print();
    std::cout << "\n";

    temp.insertAt(3, -100);
    std::cout << "After changing temp: ";
    temp.print();
    std::cout << "\n";

    std::cout << "<===Exiting the function 'testCopyConst' ====>\n";
}

int main()
{
    PtrMemberVar listOne;

    int num;
    int index;

    std::cout << "Enter (5) integers:\n";

    for (int index = 0; index < 5; index++)
    {
        std::cin >> num;
        listOne.insertAt(index, num);
    }

    std::cout << "listOne: ";
    listOne.print();
    std::cout << "\n";

    // Declare listTwo and initialize it using listOne
    PtrMemberVar listTwo(listOne);

    std::cout << "listTwo: ";
    listTwo.print();
    std::cout << "\n";

    listTwo.insertAt(5, 34);
    listTwo.insertAt(2, -76);

    std::cout << "After modifying listTwo: ";
    listTwo.print();
    std::cout << "\n";

    std::cout << "(listOne) After modifying listTwo: ";
    listOne.print();
    std::cout << "\n";

    std::cout << "Calling the function testCopyConst\n";

    // call function testCopyConst
    testCopyConst(listOne);

    std::cout << "After a call to the function: 'testCopyConst()'\nlistOne is = ";
    listOne.print();
    std::cout << "\n";

    return 0;
}
```