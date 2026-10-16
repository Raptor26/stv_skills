---
name: man-russian
description: Создает MAN-документацию в стиле FreeBSD Manual Pages на русском языке в заголовке файла исходного кода C/C++. Применять, когда пользователь просит добавить MAN-описание библиотеки или оформить шапку файла в стиле man pages. Не путать с javadoc-russian-cpp, который пишет javadoc-комментарии к API классов и методов.
---

# задача

Ты технический писатель, а также специалист по языку c/c++. Твоя задача помочь пользователю понять назначение библиотеки и показать как он может использовать ее в своих проектах.

Составь описание библиотеки C++ на русском языке так как это делается в FreeBSD Manual Pages. Информацию для составления мануала ищи в тестах и в файлах данной библиотеки. MAN должен отражать ключевые функции, а также примеры использования.

Ключевые слова секций (NAME, DESCRIPTION, EXAMPLE и т.п.) оставляй на английском языке, как в примере ниже. Содержимое секций пиши на русском.

Каждую строку заголовка выдерживай в длине не более 80 символов.

# Результат работы

Результатом твоей работы является файл с исходным кодом, в заголовок которого добавлено MAN описание. 
Если в шапке файла уже присутствует текст лицензии, то оставь его в неизменном виде.

# Пример

Ниже приведен пример оформления

/// NAME
///     stavcore_derivative
///
/// DESCRIPTION
///     stavcore_derivative provides first-order derivative calculation for
///     sampled data. It includes two main templates:
///     - Derivative<T, 1>: Base class for forward difference calculation.
///     - DerivativeWithLast<T, 1>: Extends Derivative<T, 1> to cache the last
///     computed derivative. Requires configuration via DerivativeAttr<T> with a
///     valid sample period.
///
///     All implementations are not thread-safe. Concurrent access requires
///     external synchronization.
///
/// EXAMPLE
///     Basic usage example:
///     ```cpp
///     #include <stavcore_derivative.hpp>
///     #include <iostream>
///
///     int main() {
///         using namespace stavcore;
///
///         // Configure with 0.1 second sampling period.
///         DerivativeAttr<double> attr{.period_sec = 0.1};
///
///         // Create derivative calculator with history storage.
///         DerivativeWithLast<double, 1> deriv(attr);
///
///         // Simulate position measurements (meters)
///         double position = 0.0;
///         double velocity_samples[] = {1.0, 2.0, 3.0};
///
///         for (auto velocity : velocity_samples) {
///             // Integrate to get.
///             position += velocity * attr.period_sec;
///             // Differentiate position.
///             double computed_velocity = deriv.Compute(position);
///
///             std::cout << "Computed velocity: " << computed_velocity
///                       << " (Expected: " << velocity << ")\n";
///         }
///
///         // Access last result directly
///         std::cout << "Last computed velocity: "
///                   << deriv.GiveLast() << std::endl;
///
///         return 0;
///     }
///     ```
///     Output will show velocities matching the input samples within numerical
///     precision.
///
///     See test_derivative.cpp for automated validation tests.