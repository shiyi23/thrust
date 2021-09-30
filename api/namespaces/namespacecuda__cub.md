---
title: cuda_cub
nav_exclude: true
has_children: true
has_toc: false
---

# Namespace `cuda_cub`

<code class="doxybook">
<span>namespace cuda&#95;cub {</span>
<br>
<span>template &lt;typename T&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-allocator">allocator</a></b> = <i>see below</i>;</span>
<br>
<span>template &lt;typename T&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-universal_allocator">universal&#95;allocator</a></b> = <i>see below</i>;</span>
<br>
<span>template &lt;typename T&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-pointer">pointer</a></b> = <i>see below</i>;</span>
<br>
<span>template &lt;typename T&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-universal_pointer">universal&#95;pointer</a></b> = <i>see below</i>;</span>
<br>
<span>template &lt;typename T&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-reference">reference</a></b> = <i>see below</i>;</span>
<br>
<span>template &lt;typename T,</span>
<span>&nbsp;&nbsp;typename Allocator = thrust::system::cuda::allocator&lt;T&gt;&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-vector">vector</a></b> = <i>see below</i>;</span>
<br>
<span>template &lt;typename T,</span>
<span>&nbsp;&nbsp;typename Allocator = thrust::system::cuda::universal&#95;allocator&lt;T&gt;&gt;</span>
<span>using <b><a href="/thrust/api/namespaces/namespacecuda__cub.html#using-universal_vector">universal&#95;vector</a></b> = <i>see below</i>;</span>
<br>
<span>__host__ __device__ pointer< void > </span><span><b><a href="/thrust/api/namespaces/namespacecuda__cub.html#function-malloc">malloc</a></b>(std::size_t n);</span>
<br>
<span>__host__ __device__ void </span><span><b><a href="/thrust/api/namespaces/namespacecuda__cub.html#function-free">free</a></b>(pointer< void > ptr);</span>
<span>} /* namespace cuda&#95;cub */</span>
</code>

## Types

<h3 id="using-allocator">
Type Alias <code>allocator</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T&gt;</span>
<span>using <b>allocator</b> = thrust::mr::stateless&#95;resource&#95;allocator&lt; T, thrust::system::cuda::memory&#95;resource &gt;;</span></code>
<code>cuda::allocator</code> is the default allocator used by the <code>cuda</code> system's containers such as <code>cuda::vector</code> if no user-specified allocator is provided. <code>cuda::allocator</code> allocates (deallocates) storage with <code>cuda::malloc</code> (<code>cuda::free</code>). 

<h3 id="using-universal_allocator">
Type Alias <code>universal&#95;allocator</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T&gt;</span>
<span>using <b>universal_allocator</b> = thrust::mr::stateless&#95;resource&#95;allocator&lt; T, thrust::system::cuda::universal&#95;memory&#95;resource &gt;;</span></code>
<code>cuda::universal&#95;allocator</code> allocates memory that can be used by the <code>cuda</code> system and host systems. 

<h3 id="using-pointer">
Type Alias <code>pointer</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T&gt;</span>
<span>using <b>pointer</b> = thrust::pointer&lt; T, thrust::cuda&#95;cub::tag, thrust::tagged&#95;reference&lt; T, thrust::cuda&#95;cub::tag &gt; &gt;;</span></code>
<code>cuda::pointer</code> stores a pointer to an object allocated in memory accessible by the <code>cuda</code> system. This type provides type safety when dispatching algorithms on ranges resident in <code>cuda</code> memory.

<code>cuda::pointer</code> has pointer semantics: it may be dereferenced and manipulated with pointer arithmetic.

<code>cuda::pointer</code> can be created with the function <code>cuda::malloc</code>, or by explicitly calling its constructor with a raw pointer.

The raw pointer encapsulated by a <code>cuda::pointer</code> may be obtained by eiter its <code>get</code> member function or the <code>raw&#95;pointer&#95;cast</code> function.

**Note**:
<code>cuda::pointer</code> is not a "smart" pointer; it is the programmer's responsibility to deallocate memory pointed to by <code>cuda::pointer</code>.

**Template Parameters**:
**`T`**: specifies the type of the pointee.

**See**:
* cuda::malloc 
* cuda::free 
* <a href="/thrust/api/groups/group__memory__management.html#function-raw_pointer_cast">raw_pointer_cast</a>

<h3 id="using-universal_pointer">
Type Alias <code>universal&#95;pointer</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T&gt;</span>
<span>using <b>universal_pointer</b> = thrust::pointer&lt; T, thrust::cuda&#95;cub::tag, typename std::add&#95;lvalue&#95;reference&lt; T &gt;::type &gt;;</span></code>
<code>cuda::universal&#95;pointer</code> stores a pointer to an object allocated in memory accessible by the <code>cuda</code> system and host systems.

<code>cuda::universal&#95;pointer</code> has pointer semantics: it may be dereferenced and manipulated with pointer arithmetic.

<code>cuda::universal&#95;pointer</code> can be created with <code>cuda::universal&#95;allocator</code> or by explicitly calling its constructor with a raw pointer.

The raw pointer encapsulated by a <code>cuda::universal&#95;pointer</code> may be obtained by eiter its <code>get</code> member function or the <code>raw&#95;pointer&#95;cast</code> function.

**Note**:
<code>cuda::universal&#95;pointer</code> is not a "smart" pointer; it is the programmer's responsibility to deallocate memory pointed to by <code>cuda::universal&#95;pointer</code>.

**Template Parameters**:
**`T`**: specifies the type of the pointee.

**See**:
* cuda::universal_allocator 
* <a href="/thrust/api/groups/group__memory__management.html#function-raw_pointer_cast">raw_pointer_cast</a>

<h3 id="using-reference">
Type Alias <code>reference</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T&gt;</span>
<span>using <b>reference</b> = thrust::tagged&#95;reference&lt; T, thrust::cuda&#95;cub::tag &gt;;</span></code>
<code>cuda::reference</code> is a wrapped reference to an object stored in memory accessible by the <code>cuda</code> system. <code>cuda::reference</code> is the type of the result of dereferencing a <code>cuda::pointer</code>.

**Template Parameters**:
**`T`**: Specifies the type of the referenced object.

**See**:
cuda::pointer 

<h3 id="using-vector">
Type Alias <code>vector</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T,</span>
<span>&nbsp;&nbsp;typename Allocator = thrust::system::cuda::allocator&lt;T&gt;&gt;</span>
<span>using <b>vector</b> = thrust::detail::vector&#95;base&lt; T, Allocator &gt;;</span></code>
<code>cuda::vector</code> is a container that supports random access to elements, constant time removal of elements at the end, and linear time insertion and removal of elements at the beginning or in the middle. The number of elements in a <code>cuda::vector</code> may vary dynamically; memory management is automatic. The elements contained in a <code>cuda::vector</code> reside in memory accessible by the <code>cuda</code> system.

**Template Parameters**:
* **`T`** The element type of the <code>cuda::vector</code>. 
* **`Allocator`** The allocator type of the <code>cuda::vector</code>. Defaults to <code>cuda::allocator</code>.

**See**:
* <a href="https://en.cppreference.com/w/cpp/container/vector">https://en.cppreference.com/w/cpp/container/vector</a>
* <a href="/thrust/api/classes/classhost__vector.html">host_vector</a> For the documentation of the complete interface which is shared by <code>cuda::vector</code>
* <a href="/thrust/api/classes/classdevice__vector.html">device_vector</a>
* universal_vector 

<h3 id="using-universal_vector">
Type Alias <code>universal&#95;vector</code>
</h3>

<code class="doxybook">
<span>template &lt;typename T,</span>
<span>&nbsp;&nbsp;typename Allocator = thrust::system::cuda::universal&#95;allocator&lt;T&gt;&gt;</span>
<span>using <b>universal_vector</b> = thrust::detail::vector&#95;base&lt; T, Allocator &gt;;</span></code>
<code>cuda::universal&#95;vector</code> is a container that supports random access to elements, constant time removal of elements at the end, and linear time insertion and removal of elements at the beginning or in the middle. The number of elements in a <code>cuda::universal&#95;vector</code> may vary dynamically; memory management is automatic. The elements contained in a <code>cuda::universal&#95;vector</code> reside in memory accessible by the <code>cuda</code> system and host systems.

**Template Parameters**:
* **`T`** The element type of the <code>cuda::universal&#95;vector</code>. 
* **`Allocator`** The allocator type of the <code>cuda::universal&#95;vector</code>. Defaults to <code>cuda::universal&#95;allocator</code>.

**See**:
* <a href="https://en.cppreference.com/w/cpp/container/vector">https://en.cppreference.com/w/cpp/container/vector</a>
* <a href="/thrust/api/classes/classhost__vector.html">host_vector</a> For the documentation of the complete interface which is shared by <code>cuda::universal&#95;vector</code>
* <a href="/thrust/api/classes/classdevice__vector.html">device_vector</a>
* universal_vector 


## Functions

<h3 id="function-malloc">
Function <code>cuda&#95;cub::malloc</code>
</h3>

<code class="doxybook">
<span>__host__ __device__ pointer< void > </span><span><b>malloc</b>(std::size_t n);</span></code>
Allocates an area of memory available to Thrust's <code>cuda</code> system. 
Allocates a typed area of memory available to Thrust's <code>cuda</code> system. 

**Note**:
* The <code>cuda::pointer&lt;void&gt;</code> returned by this function must be deallocated with <code>cuda::free</code>. 
* The <code>cuda::pointer&lt;T&gt;</code> returned by this function must be deallocated with <code>cuda::free</code>. 

**Function Parameters**:
* **`n`** Number of bytes to allocate. 
* **`n`** Number of elements to allocate. 

**Returns**:
* A <code>cuda::pointer&lt;void&gt;</code> pointing to the beginning of the newly allocated memory. A null <code>cuda::pointer&lt;void&gt;</code> is returned if an error occurs. 
* A <code>cuda::pointer&lt;T&gt;</code> pointing to the beginning of the newly allocated elements. A null <code>cuda::pointer&lt;T&gt;</code> is returned if an error occurs. 

**See**:
* cuda::free 
* std::malloc
* cuda::free 
* std::malloc 

<h3 id="function-free">
Function <code>cuda&#95;cub::free</code>
</h3>

<code class="doxybook">
<span>__host__ __device__ void </span><span><b>free</b>(pointer< void > ptr);</span></code>
Deallocates an area of memory previously allocated by <code>cuda::malloc</code>. 

**Function Parameters**:
**`ptr`**: A <code>cuda::pointer&lt;void&gt;</code> pointing to the beginning of an area of memory previously allocated with <code>cuda::malloc</code>. 

**See**:
* cuda::malloc 
* std::free 

