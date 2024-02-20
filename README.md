# Miscellaneous_
### function mergeOverlappingObjects(objects, currentIndex = 0) {
  // Base case: if the current index is at the end of the array
  if (currentIndex === objects.length - 1) {
    return objects;
  }

  const currentObject = objects[currentIndex];
  const nextObject = objects[currentIndex + 1];

  // Check if the current object overlaps with the next one
  if (currentObject.till >= nextObject.from) {
    // Merge the overlapping objects
    const mergedObject = {
      from: Math.min(currentObject.from, nextObject.from),
      till: Math.max(currentObject.till, nextObject.till),
    };

    // Remove the individual objects and insert the merged one
    objects.splice(currentIndex, 2, mergedObject);

    // Recursively call the function with the updated array and the same index
    return mergeOverlappingObjects(objects, currentIndex);
  } else {
    // If no overlap, move to the next index
    return mergeOverlappingObjects(objects, currentIndex + 1);
  }
}

// Example usage
const array = [
  { from: 37800000, till: 66600000 },
  { from: 41400000, till: 52200000 },
  { from: 48600000, till: 55800000 },
  // Add more objects as needed
];

const mergedArray = mergeOverlappingObjects(array);
console.log(mergedArray);
