# Techniques to render large lists
## Virtualization
Virtualization is a technique where only the visible items in a list are rendered while the rest are dynamically rendered as the user scrolls. Libraries like `react-virtualized` and `react-window` provide efficient 
components for virtualized lists. When the user scrolls, new items are rendered and old items are unmounted from the DOM, keeping the memory footprint and rendering time low.

## Pagination
Pagination is a technique used to break down a large dataset or list into smaller pages. It helps improve performance by loading and displaying a limited number of items at a time. Users can navigate through the pages using navigation controls such as previous and next buttons or page numbers. When a user interacts with the pagination controls, 
the corresponding page is loaded and rendered. This allows for efficient handling of large datasets and enhances the user experience by presenting information in manageable chunks.

## Infinite scrolling
 Infinite scrolling is a technique that allows for continuous scrolling through a large list by dynamically loading more items as the user approaches the end of the current list. Instead of splitting the list into smaller pages or sections, infinite scrolling provides a seamless scrolling experience where new items are appended to the existing list. 
 It's commonly used in scenarios like social media feeds, where new content is constantly being loaded as the user scrolls down.
