<h1>Born2beRoot</h1>

<h2>Project Overview</h2>
<p>The <code>Born2beRoot</code> project is a system administration exercise that involves setting up a server with specific requirements using virtualization software like VirtualBox or UTM.</p>

<h2>Purpose</h2>
<p>The purpose of this project is to introduce you to virtualization and system administration. You will create a virtual machine, set up an operating system with specific configurations, and implement a secure server environment.</p>

<h2>What You Will Learn</h2>
<ul>
    <li>How to use virtualization software to create and manage virtual machines.</li>
    <li>How to install and configure an operating system with specific security measures.</li>
    <li>How to set up and manage server services like SSH and firewalls.</li>
    <li>How to implement and enforce password policies and user permissions.</li>
</ul>

<h2>Project Contents</h2>

<h3>Mandatory Part</h3>
<p>You must set up a server with the following requirements:</p>
<ul>
    <li>Use VirtualBox or UTM for virtualization.</li>
    <li>Install the latest stable version of Debian or Rocky as the operating system (Debian recommended for beginners).</li>
    <li>Create at least 2 encrypted partitions using LVM.</li>
    <li>Set up an SSH service running on port 4242, without allowing root login via SSH.</li>
    <li>Configure a firewall (UFW for Debian, firewalld for Rocky) to leave only port 4242 open.</li>
    <li>Set the hostname of your virtual machine to your login ending with 42 (e.g., wil42).</li>
    <li>Implement a strong password policy with specific requirements (e.g., password expiration, minimum length, complexity).</li>
    <li>Install and configure sudo with strict rules and logging.</li>
    <li>Create a user with your login name, belonging to the user42 and sudo groups.</li>
    <li>Create a monitoring script to display system information every 10 minutes.</li>
</ul>

<h3>Bonus Part</h3>
<p>The bonus part includes additional features to enhance your server setup:</p>
<ul>
    <li>Set up partitions to match a specific structure.</li>
    <li>Set up a functional WordPress website with lighttpd, MariaDB, and PHP.</li>
    <li>Set up an additional useful service of your choice (excluding NGINX/Apache2).</li>
</ul>
<p>The bonus part will only be assessed if the mandatory part is perfect.</p>

<h2>Usage</h2>
<p>After setting up your virtual machine and server, use the configured services and monitoring script to manage and monitor your server environment.</p>

<h2>Conclusion</h2>
<p>The <code>Born2beRoot</code> project provides a comprehensive introduction to system administration and virtualization. By completing this project, you will gain valuable skills in setting up and securing a server, managing user permissions, and implementing monitoring and logging practices.</p>
