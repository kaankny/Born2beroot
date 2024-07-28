<h1>Get Next Line</h1>

<h2>Project Overview</h2>
<p>The <code>Get Next Line</code> project is about programming a function that returns a line read from a file descriptor. This project introduces the concept of static variables in C programming and aims to add a convenient function to your collection.</p>

<h2>Purpose</h2>
<p>The purpose of this project is to implement a function named <code>get_next_line</code> that reads a line from a file descriptor and returns it. This function should handle multiple calls to read an entire file line by line and manage memory efficiently.</p>

<h2>What You Will Learn</h2>
<ul>
    <li>How to use static variables in C.</li>
    <li>How to read from file descriptors in a controlled manner.</li>
    <li>How to handle memory allocation and deallocation properly.</li>
    <li>How to implement a function that can manage state across multiple calls.</li>
</ul>

<h2>Project Contents</h2>

<h3>Mandatory Part</h3>
<p>You must implement the following function:</p>
<ul>
    <li><code>get_next_line</code>: A function that reads a line from a file descriptor and returns it.</li>
</ul>

<h4>Function Prototype</h4>
<p><code>char *get_next_line(int fd);</code></p>

<h4>Parameters</h4>
<ul>
    <li><code>fd</code>: The file descriptor to read from.</li>
</ul>

<h4>Return Value</h4>
<ul>
    <li>The function returns the line read from the file descriptor.</li>
    <li>If there is nothing else to read or if an error occurs, it returns <code>NULL</code>.</li>
</ul>

<h4>External Functions</h4>
<p>You are allowed to use the following external functions:</p>
<ul>
    <li><code>read</code></li>
    <li><code>malloc</code></li>
    <li><code>free</code></li>
</ul>

<h4>Description</h4>
<ul>
    <li>Repeated calls to <code>get_next_line</code> should allow you to read a text file pointed to by the file descriptor, one line at a time.</li>
    <li>The function should return the line that was read, including the terminating <code>\n</code> character, except if the end of file was reached and does not end with a <code>\n</code> character.</li>
    <li>The header file <code>get_next_line.h</code> must at least contain the prototype of the <code>get_next_line</code> function.</li>
    <li>Add any helper functions in <code>get_next_line_utils.c</code>.</li>
</ul>

<h3>Bonus Part</h3>
<p>The bonus part includes additional features:</p>
<ul>
    <li>Develop <code>get_next_line</code> using only one static variable.</li>
    <li><code>get_next_line</code> should manage multiple file descriptors at the same time, maintaining the reading state for each.</li>
</ul>

<h4>Bonus Files</h4>
<ul>
    <li><code>get_next_line_bonus.c</code></li>
    <li><code>get_next_line_bonus.h</code></li>
    <li><code>get_next_line_utils_bonus.c</code></li>
</ul>

<p>The bonus part will only be assessed if the mandatory part is perfect.</p>

<h2>Usage</h2>
<p>To use the <code>get_next_line</code> function, include the header file and call the function with a valid file descriptor. The function reads from the file descriptor and returns the next line each time it is called.</p>

<h2>Conclusion</h2>
<p>The <code>Get Next Line</code> project is a great opportunity to learn about static variables and file descriptor handling in C. By completing this project, you will enhance your ability to manage state across multiple function calls and improve your understanding of low-level file operations.</p>
