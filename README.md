# pointers
 Experiments with C++17/20 pointers for ownership semantics, RAII

## Inspiration
C++ has had issues with consistant resource ownership and smart pointers.
But there are some really good ideas about how to handle this.
- [CppCoreGuidelines: Resource Management](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#S-resource)
- [_“Writing Good C++14”_ by Bjarne Stroustrup](https://isocpp.org/blog/2015/09/stroustrup-cppcon15-keynote)
- [_“Writing Good C++14 … By Default”_ by Herb Sutter](https://isocpp.org/blog/2015/09/sutter-cppcon15-day2plenary)

In addition, C++17 and C++20 has since added features to make this somewhat easier.

The [GSL: Guideline Support Library](https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#S-gsl)
provides a GSL definition of the **`not_null<>`** class.
This seems very interesting to me, but I think there's a useful generalization to
define a default behavior for the default constructor, instead of dis-allowing it.

## Goals
Explore the use of templates to define smart pointers that do not require ubiquitious validity tests like:
> `if (p->get() != nullptr) {` ... use the pointer ... `}`

- exception safe
- efficient
- unambiguous ownership of underlying resources
