<p align="center">
  <img alt="BigInt" src="logo.png">
</p>
<h3 align="center">Arbitrary-sized integer class for C++</h3>

---
[![Release version][release-shield]][release-link]
[![Travis status][travis-shield]][travis-link]
[![Try it online][try-online-shield]][try-online-link]
[![License][license-shield]][license-link]

:construction: Work in progress :construction:

#### Contents

* [Highlights](#highlights)
* [Usage](#usage)
* [Features](#features)
* [Compiling / testing](#compiling--testing)
* [Contributing](#contributing)
* [License](#license)

## Highlights

* No additional dependencies apart from the standard library.
* Modern C++ (compiles with C++11 / C++14 / C++17).
* No special compiling or linking required. Simply download the
  [single header file][release-link], include it in your code, and compile
  however you would.

## Usage

1. Download the [single-include header file][release-link] to a location under
    your include path. Then `#include` it in your code:
    ```C++
    #include "BigInt.hpp"   // the actual path may vary
    ```

1. Create objects of the `BigInt` class, and do what you got to do!
    ```C++
    BigInt num1, num2;
    num1 = 1234567890;
    num2 = "9876543210123456789098765432101234567890";

    std::cout << num1 * num2 * 123456 << "\n";
    // Output: 1505331490682966620443288524512589666204282352096057600
    ```

## Features

### Operators

All binary operators can have either an integer (upto `signed long long int`),
a string (`std::string` or a string literal), or another `BigInt` as the second operand.

* #### Assignment: `=`
  ```C++
  my_big_int = 1234567890;
  my_big_int = "123456789012345678901234567890";
  my_big_int = other_big_int;
  ```

* #### Unary arithmetic: `+`, `-`
  ```C++
  my_big_int = +other_big_int;  // doesn't return the absolute value
  my_big_int = -other_big_int;
  ```

* #### Binary arithmetic: `+`, `-`, `*`, `/`, `%`
  ```C++
  big_int_1 = big_int_2 + 1234567890;
  big_int_1 = big_int_2 - "123456789012345678901234567890";
  big_int_1 = big_int_2 * big_int_3;
  big_int_1 = big_int_2 / 1234567890;
  big_int_1 = big_int_2 % "123456789012345678901234567890";
  ```

* #### Arithmetic-assignment: `+=`, `-=`, `*=`, `/=`, `%=`
    ```C++
    big_int_1 += big_int_2;
    big_int_1 -= 1234567890;
    big_int_1 *= "123456789012345678901234567890";
    big_int_1 /= big_int_2;
    big_int_1 %= 1234567890;
    ```

* #### Increment and decrement: `++`, `--`
  ```C++
  some_big_int = ++my_big_int;   // pre-increment
  some_big_int = --my_big_int;   // pre-decrement

  some_big_int = my_big_int++;   // post-increment
  some_big_int = my_big_int--;   // post-decrement
  ```

* #### Relational: `<`, `>`, `<=`, `>=`, `==`, `!=`
  ```C++
  if (big_int_1 < 1234567890
      or big_int_1 > "123456789012345678901234567890"
      or big_int_1 <= big_int_2
      or big_int_1 >= 1234567890
      or big_int_1 == "123456789012345678901234567890"
      or big_int_1 != big_int_3) {
      ...
  }
  ```

* #### I/O stream: `<<`, `>>`
  ```C++
  std::cout << big_int_1 << ", " << big_int_2 << "\n";
  output_file << big_int_1 << ", " << big_int_2 << "\n";

  std::cin >> big_int_1 >> big_int_2;
  input_file >> big_int_1 >> big_int_2;
  ```

### Functions

* #### Conversion: `to_string`, `to_int`, `to_long`, `to_long_long`
  Convert a `BigInt` to either a `string`, `int`, `long`, or `long long`.

  **Note**: If the `BigInt` is beyond the range of the target type, an
  [out_of_range exception][out_of_range-exception] is thrown.

    ```C++
    some_str = my_big_int.to_string();

    some_int = my_big_int.to_int();

    some_long = my_big_int.to_long();

    some_long_long = my_big_int.to_long_long();
    ```

* #### Math

  * #### `abs`
    Get the absolute value of a `BigInt`.

    ```C++
    my_big_int = abs(other_big_int);
    ```

  * #### `big_pow10`
    Get a `BigInt` equal to 10<sup>x</sup>.

    ```C++
    my_big_int = big_pow10(5000);   // my_big_int = 10^5000
    ```

## Compiling / testing

Since this project is built as a library, there are no source files.
However, there are unit tests for each header file that the project is split into.
* To compile the tests, run **`make`**.
* To build and run the tests, run **`make test`**.

You will need to run **`make`** at least once before you can run **`make test`**.

## Contributing

Please read the [contributing guidelines][contributing-link] for details on
how to contribute to the project.

## License

This project is licensed under the terms of the [MIT license][license-link].

## Authors

* **Shubham Garg**  - [shubhamgarg9](https://github.com/shubhamgarg9) 


[release-shield]: https://img.shields.io/github/release/faheel/BigInt/all.svg?style=for-the-badge
[release-link]: https://github.com/faheel/BigInt/releases
[travis-shield]: https://img.shields.io/travis/faheel/BigInt.svg?style=for-the-badge
[travis-link]: https://travis-ci.org/faheel/BigInt
[try-online-shield]: https://img.shields.io/badge/Try_online-Wandbox-E91E63.svg?style=for-the-badge
[try-online-link]: https://wandbox.org/permlink/J9eEgFpryxDwc3th
[license-shield]: https://img.shields.io/github/license/faheel/BigInt.svg?style=for-the-badge
[license-link]: https://github.com/faheel/BigInt/blob/master/LICENSE
[out_of_range-exception]: http://en.cppreference.com/w/cpp/error/out_of_range
[contributing-link]: https://github.com/faheel/BigInt/blob/master/CONTRIBUTING.md
