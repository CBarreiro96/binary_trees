<img src="https://user-images.githubusercontent.com/66263776/98416555-43fa9b80-204d-11eb-800a-df8e19b62655.jpg" width="700" height= "200">

# 0x1D. C - Binary trees
<p align="center">
<img src="https://user-images.githubusercontent.com/66263776/100120963-90fcb100-2e46-11eb-802a-891f060e49d1.png" width="600" height= "300">
</p>

## :notebook_with_decorative_cover: Glossary :notebook_with_decorative_cover:
<p align="center">
<img src="https://user-images.githubusercontent.com/66263776/100281718-6f7bf200-2f38-11eb-995f-2a96d4e22fb5.png" width="200" height= "150">
</p>

* **ROOT:** is the node with no parents. How you can see the image is A
* **LEAF** is a node with no children. In the image we can E, J, K ,H and I are leaf.
* **DEPTH OF A NODE** is the length of the path from the root to the node
* **HEIGHT OF A NODE** is the length of the path from that node to the deepest node. For example in the image the height of B is 2 (B – F – J).
* **SIZE OF A NODE** is the number of of descendants it has including itself for example the size of the subtree C is 3
* **FULL NODE** are nodes which has both left and right children as non-empty.
* **PERFECT BINARY TREE**  is a type of binary tree in which every internal node has exactly two child nodes and all the leaf nodes are at the same level.
<p align="center">
<img src="https://user-images.githubusercontent.com/66263776/100295041-8a5d5f00-2f56-11eb-8bfd-f137135ce5ff.png" width="150" height= "100">
</p>

* **SIBLING** are children of same parent 


## :memo: Description about activities :memo:
In this repository you can find some exercise of Binery trees, I mean , It is a introduccion about binary tree. IN follow item.
## :book: Information :book:



### :interrobang: Question :thinking:
#### [New node](https://github.com/CBarreiro96/binary_trees/blob/master/0-binary_tree_node.c)
Write a function that creates a binary tree node
* Prototype: binary_tree_t *binary_tree_node(binary_tree_t *parent, int value);
* Where parent is a pointer to the parent node of the node to create
* And value is the value to put in the new node
* When created, a node does not have any child
* Your function must return a pointer to the new node, or NULL on failure
```
user@/tmp/binary_trees$ cat 0-main.c 
#include <stdlib.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);

    root->left = binary_tree_node(root, 12);
    root->left->left = binary_tree_node(root->left, 6);
    root->left->right = binary_tree_node(root->left, 16);

    root->right = binary_tree_node(root, 402);
    root->right->left = binary_tree_node(root->right, 256);
    root->right->right = binary_tree_node(root->right, 512);

    binary_tree_print(root);
    return (0);
}
user@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 0-main.c 0-binary_tree_node.c -o 0-node
user@/tmp/binary_trees$ ./0-node
       .-------(098)-------.
  .--(012)--.         .--(402)--.
(006)     (016)     (256)     (512)
alex@/tmp/binary_trees$
```

#### [Insert left](https://github.com/CBarreiro96/binary_trees/blob/master/1-binary_tree_insert_left.c)
Write a function that inserts a node as the left-child of another node

* Prototype: binary_tree_t *binary_tree_insert_left(binary_tree_t *parent, int value);
* Where parent is a pointer to the node to insert the left-child in
* And value is the value to store in the new node
* Your function must return a pointer to the created node, or NULL on failure or if parent is NULL
* If parent already has a left-child, the new node must take its place, and the old left-child must be set as the left-child of the new node.
```
user@/tmp/binary_trees$ cat 1-main.c 
#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_print(root);
    printf("\n");
    binary_tree_insert_left(root->right, 128);
    binary_tree_insert_left(root, 54);
    binary_tree_print(root);
    return (0);
}
user@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 1-main.c 1-binary_tree_insert_left.c 0-binary_tree_node.c -o 1-left
alex@/tmp/binary_trees$ ./1-left
  .--(098)--.
(012)     (402)

       .--(098)-------.
  .--(054)       .--(402)
(012)          (128)                                            
user@/tmp/binary_trees$
```
#### [Insert right](https://github.com/CBarreiro96/binary_trees/blob/master/2-binary_tree_insert_right.c)
Write a function that inserts a node as the right-child of another node

* Prototype: binary_tree_t *binary_tree_insert_right(binary_tree_t *parent, int value);
* Where parent is a pointer to the node to insert the right-child in
* And value is the value to store in the new node
* Your function must return a pointer to the created node, or NULL on failure or if parent is NULL
* If parent already has a right-child, the new node must take its place, and the old right-child must be set as the right-child of the new node.
```
user@/tmp/binary_trees$ cat 2-main.c 
#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_print(root);
    printf("\n");
    binary_tree_insert_right(root->left, 54);
    binary_tree_insert_right(root, 128);
    binary_tree_print(root);
    return (0);
}
user@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 2-main.c 2-binary_tree_insert_right.c 0-binary_tree_node.c -o 2-right
alex@/tmp/binary_trees$ ./2-right 
  .--(098)--.
(012)     (402)

  .-------(098)--.
(012)--.       (128)--.
     (054)          (402)
alex@/tmp/binary_trees$
```
#### [Delete](https://github.com/CBarreiro96/binary_trees/blob/master/3-binary_tree_delete.c)

#### [Is leaf]()
Write a function that checks if a node is a leaf

* Prototype: int binary_tree_is_leaf(const binary_tree_t *node);
* Where node is a pointer to the node to check
* Your function must return 1 if node is a leaf, otherwise 0
* If node is NULL, return 0
```
user@/tmp/binary_trees$ cat 4-main.c 
#include <stdlib.h>
#include <stdio.h>
#include "binary_trees.h"

/**
 * main - Entry point
 *
 * Return: Always 0 (Success)
 */
int main(void)
{
    binary_tree_t *root;
    int ret;

    root = binary_tree_node(NULL, 98);
    root->left = binary_tree_node(root, 12);
    root->right = binary_tree_node(root, 402);
    binary_tree_insert_right(root->left, 54);
    binary_tree_insert_right(root, 128);
    binary_tree_print(root);

    ret = binary_tree_is_leaf(root);
    printf("Is %d a leaf: %d\n", root->n, ret);
    ret = binary_tree_is_leaf(root->right);
    printf("Is %d a leaf: %d\n", root->right->n, ret);
    ret = binary_tree_is_leaf(root->right->right);
    printf("Is %d a leaf: %d\n", root->right->right->n, ret);
    return (0);
}
user@/tmp/binary_trees$ gcc -Wall -Wextra -Werror -pedantic binary_tree_print.c 4-binary_tree_is_leaf.c 4-main.c 0-binary_tree_node.c 2-binary_tree_insert_right.c -o 4-leaf
alex@/tmp/binary_trees$ ./4-leaf 
  .-------(098)--.
(012)--.       (128)--.
     (054)          (402)
Is 98 a leaf: 0
Is 128 a leaf: 0
Is 402 a leaf: 1
user@/tmp/binary_trees$

```