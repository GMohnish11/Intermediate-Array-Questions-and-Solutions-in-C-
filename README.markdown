# CPP-Array-Questions

## Overview
This repository, `CPP-Array-Questions`, contains a collection of intermediate-level array problems and their solutions in C++, developed by Mohnish Gupta. Designed for students, developers, and coding enthusiasts, it includes problems like array rotation, Kadane’s algorithm, and searching in rotated arrays, with detailed explanations and efficient C++ code. Ideal for practicing data structures, preparing for coding interviews, or competitive programming.

## Description
A collection of intermediate C++ array problems with solutions, including rotation, Kadane’s algorithm, and more. Ideal for coding practice and interviews, by Mohnish Gupta.

## Features
- **Intermediate Problems**: Covers array manipulation techniques like rotation, subarray sums, and searching in rotated arrays.
- **C++ Solutions**: Efficient, well-commented code using modern C++ (e.g., `std::vector`, range-based loops).
- **Explanations**: Each problem includes a description, solution, time/space complexity, and edge case analysis.
- **Markdown Documentation**: Problems and solutions are detailed in `cpp_array_questions.md` for easy reference.
- **Testable Code**: Includes a `main.cpp` driver file to test solutions with custom inputs.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/GMohnish11/CPP-Array-Questions.git
   cd CPP-Array-Questions
   ```
2. **Ensure C++ Compiler**:
   - Install a C++ compiler (e.g., `g++` via GCC) if not already present.
   - Verify: `g++ --version`.
3. **Compile and Run**:
   - Compile a specific solution:
     ```bash
     g++ solutions/solution1_rotate_array.cpp -o rotate_array
     ./rotate_array
     ```
   - Or use `main.cpp` to test all solutions:
     ```bash
     g++ main.cpp -o test
     ./test
     ```

## Usage
### Exploring Problems
- Read `cpp_array_questions.md` for problem descriptions, solutions, and explanations.
- Problems include:
  1. Rotate Array by K Positions
  2. Find Maximum Subarray Sum (Kadane’s Algorithm)
  3. Search in a Sorted and Rotated Array
  4. Merge Two Sorted Arrays Without Extra Space
  5. Find the Missing Number in an Array

### Running Solutions
- Each solution is in the `solutions/` directory (e.g., `solution1_rotate_array.cpp`).
- Modify `main.cpp` to test different inputs:
  ```cpp
  #include <vector>
  #include "solutions/solution1_rotate_array.cpp"
  int main() {
      std::vector<int> arr = {1, 2, 3, 4, 5};
      int k = 2;
      rotateArray(arr, k);
      for (int x : arr) std::cout << x << " "; // Output: 4 5 1 2 3
      return 0;
  }
  ```
- Compile and run as shown in the Installation section.

## Directory Structure
```
├── solutions/
│   ├── solution1_rotate_array.cpp    # Rotate array by k positions
│   ├── solution2_max_subarray_sum.cpp # Kadane’s algorithm
│   ├── solution3_search_rotated.cpp   # Search in rotated array
│   ├── solution4_merge_arrays.cpp     # Merge sorted arrays
│   ├── solution5_missing_number.cpp   # Find missing number
├── main.cpp                          # Driver code to test solutions
├── cpp_array_questions.md            # Problem descriptions and solutions
├── README.md                         # This file
└── LICENSE                           # MIT License
```

## Contributing
Contributions are welcome! To contribute:
1. Fork the repository.
2. Create a branch: `git checkout -b feature/new-problem`.
3. Add your problem and solution in `solutions/` and update `cpp_array_questions.md`.
4. Commit changes: `git commit -m "Add new array problem"`.
5. Push: `git push origin feature/new-problem`.
6. Submit a Pull Request.

Report issues via the [Issues](https://github.com/GMohnish11/CPP-Array-Questions/issues) tab.

## License
Licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments
- **Author**: Mohnish Gupta
- **Institution**: St. Peter's Engineering College, Hyderabad
- **Inspiration**: Competitive programming platforms like LeetCode, HackerRank, and GeeksforGeeks
- **Resources**: C++ Standard Library and algorithm design references

## Contact
For inquiries, contact Mohnish Gupta via GitHub issues or St. Peter's Engineering College, Hyderabad.