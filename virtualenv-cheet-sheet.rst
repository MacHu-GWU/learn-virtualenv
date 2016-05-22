virtualenv的一些常用技巧
=======================================================================
Reference: https://virtualenv.pypa.io/en/latest/

virtualenv是一个Python工具, 主要解决的是你的不同项目对第三方扩展包有着不同的依赖需求和冲突的问题。它可以为你的项目创建不同的虚拟环境, 使得让你为不同的项目创建干净的虚拟环境, 配置所需的依赖, 并保证同一台机器上多个项目不会互相冲突。AWS的beanstalk以及lambda服务会需要用到virtualenv。


基础操作
-----------------------------------------------------------------------


创建环境
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: console

	virtualenv env


**使用指定的Python可执行文件创建指定版本的虚拟环境**

Linux:

.. code-block:: console

	virtualenv -p /usr/lib/python2.7 <path-to-venv>

Windows:

.. code-block:: console

	virtualenv -p C:\Python27\python.exe <path-to-venv>


**包含系统上已安装的包**

假如你的系统上已经预装了一些包, 而你想要将这些包都预装到你的虚拟环境下, 那么你只需要在声明你的虚拟环境路径的前面加上参数 ``--system-site-packages`` 即可。最终的命令看起来像:

.. code-block:: console

	virtualenv --system-site-packages <path-to-venv>


激活环境
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Linux:

.. code-block:: console

	source bin/activate

Windows:

.. code-block:: console

	Scripts\activate


退出环境
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
.. code-block:: console

	deactivate


在虚拟环境下安装第三方包
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
在激活虚拟环境之后使用pip命令安装的第三方包, 其实都是安装在了虚拟环境下, 而不是安装在全局环境中。至于某些比较难安装的第三方包的安装方法, 将单独介绍。


在虚拟环境下运行Python
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
``python script.py``