# Page-Replacement-Policy
FIFO, LRU, LFU page replacement policy algorithms in Java

PAGE REPLACEMENT POLICIES

PAGE REPLACEMENT POLICIES

- When page fault occurs, the referenced page must be loaded.
- If there is no available frame in memory, then one page is selected for replacement.
- If the selected page has been modified, it must be copied back to disk (swapped out).
- A page replacement algorithm is said to satisfy the inclusion property or is called a stack algorithm if the set of pages in an n-frame 
  memory is always a subset of the pages in a (n + 1) frame memory.

1. FIFO (First IN, First OUT)

 * FIFO implements a queue.
 * A FIFO replacement algorithm links with each page the time when that page was added into the memory
 * The oldest page is chosen when a page is going to be replaced. We can create a FIFO queue to hold all the pages present in the memory
   disk. At the head of the queue we replace the page. We insert page at the tail of the queue when a page is added in into the memory disk.
 * Implementation:
   - Two arrays, page[n] and frame[f_size] (queue), where n is the number of pages and f_size is the size of the frame buffer
   - When there is page fault, it replaces the page in the frame after the previously replaced frame

2. LRU (Least Recently Used)

 * On a page fault, the frame that was least recently used is replaced.
 * Implementation:
   - Two arrays, page[n] and frame[f_size] (queue), where n is the number of pages and f_size is the size of the frame buffer 
   - Two additional arrays, a[f_size] & b[f_size], where a[] stores the sorted list of pages from most recently used to least recently used and b is the temporary array used to update the list
   - When page fault occurs, it finds the index of the LRU from frame[] based on the last element of a[] and replaces that page
   - Each time a page is referenced, update a[]

3. LFU (Least Frequently Used)

 * The page which has the smallest count is going to be replaced. The reason for this selection is that a mostly used page should have a 
   larger reference count.
 * This algorithm suffers from the situation in which a page is used heavily during the staring phase of aprocess, but then is never again. 
   Since it was used heavily, it has a large frequency count and remains in memory even if it is no longer needed.
 * Implemention:
   - Two arrays, page[n] and frame[f_size], where n is the number of pages and f_size is the size of the frame buffer
   - An array cnt[f_size] is used to store and keep track of the tally or frequency of usage of the pages
   - When a page fault occurs, it replaces the page with the least frequency of usage
   - If there are more than 1 page that that the least frequency of usage, use FIFO logic and replace the page that came first among those least frequently used pages.
