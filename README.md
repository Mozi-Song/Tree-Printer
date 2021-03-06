# Tree-Printer
*A Java Utility to Visualize a Node-based Tree Structure*

The node content could be anything that's printable. For example, it could be a tree of integers:
```
                                                7                                               
                        ┌───────────────────────┴───────────────────────┐                       
                        3                                              15                       
            ┌───────────┴───────────┐                       ┌───────────┴───────────┐           
            1                       5                      11                      17           
      ┌─────┴─────┐           ┌─────┴─────┐           ┌─────┴─────┐           ┌─────┴─────┐     
      0           2           4           6           9          13          16          18     
                                                   ┌──┴──┐     ┌──┴──┐                    └──┐  
                                                   8    10    12    14                      19  
```
Also, it could be a tree of strings:
```
                                      host3                                     
                    ┌───────────────────┴───────────────────┐                   
                  host1                                   host7                 
          ┌─────────┴─────────┐                   ┌─────────┴─────────┐         
        host0               host2               host5               host8       
                                             ┌────┴────┐              └────┐    
                                           host4     host6               host9  
```
The printer works best with an *almost-full (or balanced)* tree, since it draws the tree line-by-line, taking the width of a full last-level as the line width. Printing a biased tree will work too although you would have to have a very wide sheet for display.
```
                                                1                                               
                                                └───────────────────────┐                       
                                                                        2                       
                                                                        └───────────┐           
                                                                                    3           
                                                                                    └─────┐     
                                                                                          4     
                                                                                          └──┐  
                                                                                             5 
```
## How To Use 
Usage only requires two simple steps.
1. Have your tree node implement the `PrintableNode` interface.
```
public interface PrintableNode{
  PrintableNode getLeft();
  PrintableNode getRight();
  String getText();
}
```
2. Call the static `print` method in [TreePrinter](https://github.com/Mozi-Song/Tree-Printer/blob/master/TreePrinter/src/mightypork/TreePrinter.java).
```
MyTree<String> tree = new MyTree<>();
constructTree(tree);
TreePrinter.print(tree.root);
```
If you're seeing something like ??????????, make sure that your code that calls the printer is saved in UTF-8.
## Motivation & Credit
This `TreePrinter` is actually ported from this [stackoverflow answer](https://stackoverflow.com/a/29704252/3585176) by [MightyPork](https://github.com/MightyPork?utf8=%E2%9C%93&tab=repositories&q=&type=&language=).

While trying to learn different tree structures (BST, AVL Tree, etc.) by implementing them, I find it difficult to see the correctness of the resulting tree just by seeing it in the Eclipse debug window. I wrote a `toString()` method for my AVL tree, it took me almost two days, the code was not elegant, and the result was not beautifully aligned. After searching for a while, I found MightyPork's answer on stackoverflow which best fit my requirements (in an aesthetic way). It uses a concise algorithm to print out the tree structure in a self-adaptive way which adapts the node width and distances between nodes to the maximum node length -- it's "expandable"!

This visualizer could be used in similar ways: to see the correctness of your self-implemented tree, to view the structure of the tree, etc.

