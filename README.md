# Page-Replacement-Policy
FIFO, LRU, LFU page replacement policy algorithms in Java

PAGE REPLACEMENT POLICIES

- When page fault occurs, the referenced page must be loaded.
- If there is no available frame in memory, then one page is selected for replacement
- If the selected page has been modified, it must be copied back to disk (swapped out)
- A page replacement algorithm is said to satisfy the inclusion property or is called a stack algorithm if the set of pages in an n-frame 
  memory is always a subset of the pages in a (n + 1) frame memory.

1. FIFO (First IN, First OUT)

 * A FIFO replacement algorithm links with each page the time when that page was added into the memory
 * The oldest page is chosen when a page is going to be replaced. We can create a FIFO queue to hold all the pages present in the memory
   disk. At the head of the queue we replace the page. We insert page at the tail of the queue when a page is added in into the memory disk.

2. LRU (Least Recently Used)

 * On a page fault, the frame that was least recently used is replaced.
 * Implementation:
   - Add a register to every page frame - contain the last time that the page in that frame was accessed
   - Use a "logical clock" that advance by 1 tick each time a memory reference is made.
   - Each time a page is referenced, update its register

3. LFU (Least Frequently Used)

 * The page which has the smallest count is going to be replaced. The reason for this selection is that a mostly used page should have a 
   larger reference count.
 * This algorithm suffers from the situation in which a page is used heavily during the staring phase of aprocess, but then is never again. Since it was used heavily, it has a large frequency count and remains in memory even if it is no longer needed.
