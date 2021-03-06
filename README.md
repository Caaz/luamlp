luamlp
==

Luamlp is a module written in Lua, implements the algorithm
of multilayer perceptron with back-propagation algorithm in a
generic way.
One can define the number of hidden layers to 1 or 2 (not require
the use of more than two hidden layers). One can also define the
number of neurons used in any layer. The data input and output
(for training) must be formatted in a two-dimensional array format:
	
Data_input = {{x1},... {xn}} or {{x1,x2} ..., {xn-1, xn}}

Data_output y1 = {{y1},... {yn}} or {{y1,y2} ..., {yn-1, yn}}

DEPENDENCIES
--
Lua installed in system.<br>
Tested in Lua 5.1 and 5.2<br>
Linux/Ubuntu: sudo apt-get install lua5.2<br>
or<br>
sudo apt-get install lua5.1<br>

FUNCTIONS | RETURN 
--
Narray(nl, nc, value) -> table <br>
Luamlp:New(ni, nh1, nh2, nout) -> number<br>
Luamlp:Config(lr, it, bias, ert, mm, mt, fx, dfx) -> table<br>
Luamlp:LoadConfig(name(optional)) -> None <br>
Luamlp:Training(print_error) -> None <br>
Luamlp:Propagation(x) -> table <br>
Luamlp:Backpropagation(y) -> number <br>
Luamlp:Test(dinput) -> None <br> <br>


Files:
--
luamlp.lua: source code <br> 
test_luamlp.lua: file test of luamlp.lua <br>
config.luamlp: optional, file for configuration parameters luamlp.lua <br>


Example of use:
--

The XOR Problem: http://home.agh.edu.pl/~vlsi/AI/xor_t/en/main.htm

Run test_luamlp.lua:
--

In terminal enter the directo luary where Luamlp, digit:
> $ lua5.2 test_luamlp.lua <br>


Solution using Luamlp
--

<b> Detais of example XOR: </b> <br>

| input | output |<br>
 0,0 = 0 <br>
 0,1 = 1<br>
 1,0 = 1<br>
 1,1 = 0<br>


> <b> load module in variable </b> <br>
> luamlp = require 'luamlp' <br>
> <b> create neural network with 2 neuron in layer input<br>
> 2 neuron in layer hidden 1, 0 neuron in layer hidden 2<br>
> and 1 neuron in layer ouput</b> <br>
> mlp = luamlp:New(2,2,0,1)<br>
> <b>insert to input and output in neural network</b> <br>
> mlp.input = {{0,0}, {0,1}, {1,0}, {1,1}}<br>
> mlp.output = {{0}, {1}, {1}, {1}}<br>
> <b> configure os parameters mlp<br>
> 0.3 = learning rate, 10000 = iteration max.<br>
> 1 = value for bias, 0.01: error in training<br>
> 0.003: rate of mommentum term </b> <br>
> mlp:Config(0.3, 10000, 1, 0.01, 0.003)<br>
> <b> execute training, parameter true: displays error in each iteration </b> <br>
> mlp:Training(true)<br>
> <b> test of learning </b><br>
> mlp:Test(mlp.input)<br>

<br>

Using File of configuration, config.luamlp
--

Can use a special file that contains a table, <br>
table where the keys are the parameters of the neural network. <br>

<b>Config.luamlp</b> file, can create activation functions and other options <br>
to modify the behavior of the neural network, without modifying the original stand.<br>
The filename 'config.luamlp' is the default name, if he cares for your application, <br> 
simply called function:

> mlp:loadConfig() <br>

after creating a neural network. If you use another file, such as <i>'load.txt'</i> <br>
just in function call loadConfig pass a string with the file name, example:

> mlp:loadConfig('load.txt')




