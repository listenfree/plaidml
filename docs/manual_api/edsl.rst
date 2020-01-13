====
EDSL
====

Embedded Domain Specific Language

.. contents::

-------
Initialization
-------

.. tabs::

   .. group-tab:: C++

      .. doxygenfunction:: plaidml::edsl::init

   .. group-tab:: Python

      .. autofunction:: plaidml2.edsl.__init

-------
Objects
-------

.. tabs::
   .. group-tab:: C++

      .. doxygengroup:: edsl_objects
         :content-only:
         :members:

   .. group-tab:: Python

      .. autoclass:: plaidml2.edsl.IndexedTensor
      .. autoclass:: plaidml2.edsl.LogicalShape
         :members:
      .. autoclass:: plaidml2.edsl.Tensor
      .. autoclass:: plaidml2.edsl.TensorRef
      .. autoclass:: plaidml2.edsl.ProgramArgument
      .. autoclass:: plaidml2.edsl.Program
      .. autoclass:: plaidml2.edsl.TensorDim
      .. autoclass:: plaidml2.edsl.TensorIndex
      .. autoclass:: plaidml2.edsl.Constraint

----------
Primitives
----------

.. tabs::
   .. group-tab:: C++

      .. doxygengroup:: edsl_primitives
         :content-only:

   .. group-tab:: Python

      .. autofunction:: plaidml2.edsl.abs
      .. autofunction:: plaidml2.edsl.as_float
      .. autofunction:: plaidml2.edsl.as_int
      .. autofunction:: plaidml2.edsl.as_uint
      .. autofunction:: plaidml2.edsl.as_bool
      .. autofunction:: plaidml2.edsl.cos
      .. autofunction:: plaidml2.edsl.cosh
      .. autofunction:: plaidml2.edsl.exp
      .. autofunction:: plaidml2.edsl.gather
      .. autofunction:: plaidml2.edsl.ident
      .. autofunction:: plaidml2.edsl.index
      .. autofunction:: plaidml2.edsl.log
      .. autofunction:: plaidml2.edsl.pow
      .. autofunction:: plaidml2.edsl.prng
      .. autofunction:: plaidml2.edsl.reshape
      .. autofunction:: plaidml2.edsl.reshape
      .. autofunction:: plaidml2.edsl.scatter
      .. autofunction:: plaidml2.edsl.select
      .. autofunction:: plaidml2.edsl.shape
      .. autofunction:: plaidml2.edsl.sin
      .. autofunction:: plaidml2.edsl.sinh
      .. autofunction:: plaidml2.edsl.sqrt
      .. autofunction:: plaidml2.edsl.tan
      .. autofunction:: plaidml2.edsl.tanh

--------
Examples
--------

.. code-block:: c++

   Tensor sum_over_axis(const Tensor& I) {
      TensorDim M, N;
      TensorIndex m, n;
      I.bind_dims(M, N);
      auto O = TensorOutput(N);
      O(n) += I(m, n); // contraction
      return O;
   }

.. math::
   \color{red}O[n]
   \color{default}=
   \color{green}\sum_{m}
   \color{blue}I[m, n]

.. math::
   \color{red}\verb|O(n)|
   \color{green}\verb| += |
   \color{blue}\verb|I(m, n)|\color{default}\verb|;|
