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
## How To Use the Tree-Printer
Usage only requires two simple steps.
1. Have your tree node implement the `PrintableNode` interface.
```
public interface PrintableNode{
  PrintableNode getLeft();
  PrintableNode getRight();
  String getText();
}
```
2. Call the static `print` method in `TreePrinter`.
```
MyTree<String> tree = new MyTree<>();
constructTree(tree);
TreePrinter.print(tree.root);
```
## Motivation & Credit
This `TreePrinter` is actually ported from this [stackoverflow answer](https://stackoverflow.com/a/29704252/3585176) by [MightyPork](https://github.com/MightyPork?utf8=%E2%9C%93&tab=repositories&q=&type=&language=).

While trying to learn different tree structures (BST, AVL Tree, etc.) by implementing them, I find it difficult to see the correctness of the resulting tree just by seeing it in the Eclipse debug window. I wrote a `toString()` method for my AVL tree, it took me almost two days, the code was not elegant, and the result was not beautifully aligned. After searching for a while, I found MightyPork's answer on stackoverflow which best fit my requirements (in an aesthetic way).


