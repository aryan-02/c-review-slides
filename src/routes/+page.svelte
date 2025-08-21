<script lang="ts">
	// @ts-ignore
	// import { fragment } from '$animotion';
	import { Presentation, Slide, Code, Transition, Action } from '@animotion/core'
	import { base } from '$app/paths';
	let text1: HTMLParagraphElement
	let text2: HTMLParagraphElement
	let text3: HTMLParagraphElement
	let text4: HTMLParagraphElement
	let code: ReturnType<typeof Code>

	let codeannot_preprocessor: HTMLParagraphElement
	let codeannot_main_function: HTMLParagraphElement
	let code_conditional: ReturnType<typeof Code>
	let code_loop_example: ReturnType<typeof Code>
	let code_assignment_associativity: ReturnType<typeof Code>

	let code_function: ReturnType<typeof Code>
	let code_array_iter: ReturnType<typeof Code>
	let code_structs: ReturnType<typeof Code>
	let code_ptrarray: ReturnType<typeof Code>
</script>

<Presentation
	options={{
		history: true,
		transition: 'slide',
		controls: true,
		progress: true,
		autoAnimateDuration: 0.4,
		viewDistance: 2,
		help: true
	}}
>
	<Slide class="h-full place-content-center place-items-center">
		<h1 class="p-3 text-7xl font-thin">Algorithms and Data Structures</h1>
		<h3 class="p-3">C Review 💻</h3>
		<h5 class="p-3">Aryan Mediratta</h5>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1 class="mb-4">Here's what we'll do.</h1>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1 class="mb-4">Here's what we'll do.</h1>
		<p class="raw-bullet">A quick review of C fundamentals</p>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1 class="mb-4">Here's what we'll do.</h1>
		<p class="raw-bullet opacity-60">A quick review of C fundamentals</p>
		<p class="raw-bullet">Expressions, statements, lvalues, and rvalues</p>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1 class="mb-4">Here's what we'll do.</h1>
		<p class="raw-bullet opacity-60">A quick review of C fundamentals</p>
		<p class="raw-bullet opacity-60">Expressions, statements, lvalues, and rvalues</p>
		<p class="raw-bullet">Structs and Pointers</p>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1 class="mb-4">Here's what we'll do.</h1>
		<p class="raw-bullet opacity-60">A quick review of C fundamentals</p>
		<p class="raw-bullet opacity-60">Expressions, statements, lvalues, and rvalues</p>
		<p class="raw-bullet opacity-60">Structs and Pointers</p>
		<p class="raw-bullet">UNIX review and debugging</p>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1 class="mb-4">Here's what we'll do.</h1>
		<p class="raw-bullet opacity-60">A quick review of C fundamentals</p>
		<p class="raw-bullet opacity-60">Expressions, statements, lvalues, and rvalues</p>
		<p class="raw-bullet opacity-60">Structs and Pointers</p>
		<p class="raw-bullet opacity-60">UNIX review and debugging</p>
		<p class="raw-bullet">Good coding practices</p>
	</Slide>
	<Slide class="h-full place-content-center">
		<Transition visible>
			<h1>The Build Process 🔧</h1>
		</Transition>
		<Transition>
			<img src="images/c_build_process.png" class="w-2xl" alt="" />
		</Transition>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Code
			bind:this={code}
			class="flex-1/2"
			lang="c"
			theme="andromeeda"
			code={`
				#include <stdio.h>

				int main(void)
				{
					printf("Hello, CSE 3318! 👋\\n");
					return 0;
				}
			`}
			options={{ duration: 1000, stagger: 0.3, lineNumbers: true, containerStyle: true }}
		/>
	</Slide>
	<Slide animate class="h-full grid-cols-2 place-content-center place-items-center">
		<Code
			bind:this={code}
			class="flex-1/2"
			lang="c"
			theme="andromeeda"
			code={`
				#include <stdio.h>

				int main(void)
				{
					printf("Hello, CSE 3318! 👋\\n");
					return 0;
				}
			`}
			options={{ duration: 1000, stagger: 0.3, lineNumbers: true, containerStyle: true }}
		/>
		<div class="flex-1/2">
			<Transition do={() => code.selectLines`1`} undo={() => code.selectLines`*`}>
				<p bind:this={codeannot_preprocessor}>Preprocessor Directive</p>
			</Transition>
			<Transition
				do={() => {
					code.selectLines`3,6`
					codeannot_preprocessor.classList.add('hidden')
				}}
				undo={() => {
					code.selectLines`1`
					codeannot_preprocessor.classList.remove('hidden')
				}}
			>
				<p bind:this={codeannot_main_function}>Main Function</p>
			</Transition>
			<Transition
				do={() => {
					code.selectLines`5`
					codeannot_main_function.classList.add('hidden')
				}}
				undo={() => {
					code.selectLines`3,6`
					codeannot_main_function.classList.remove('hidden')
				}}
			>
				<p>Function call to <span class="ctype">printf()</span></p>
			</Transition>
		</div>
	</Slide>
	<Slide class="h-full place-content-center">
		<Slide class="h-full place-content-center">
			<h1>C Tokens 🎟️</h1>
			<p class="p-3">Tokens are the smallest unit of a programming language.</p>
		</Slide>
		<Slide class="h-full place-content-center">
			<h1>C Tokens 🎟️</h1>
			<ul class="text-left">
				<li class="p-1.5">Keywords 🔑</li>
				<li class="p-1.5">Identifiers 🪪</li>
				<li class="p-1.5">Constants 2️⃣</li>
				<li class="p-1.5">Operators ➕</li>
				<li class="p-1.5">Delimiters ✂️</li>
			</ul>
		</Slide>
		<Slide class="h-full place-items-center">
			<div class="grid-1/5"></div>
			<h1>C Keywords 🔑</h1>
			<div class="flex w-full justify-evenly">
				<ul class="text-lg list-none text-left font-mono">
					<li>alignas (C23)</li>
					<li>alignof (C23)</li>
					<li>auto</li>
					<li>bool (C23)</li>
					<li>break</li>
					<li>case</li>
					<li>char</li>
					<li>const</li>
					<li>constexpr (C23)</li>
					<li>continue</li>
					<li>default</li>
					<li>do</li>
					<li>double</li>
					<li>else</li>
					<li>enum</li>
				</ul>
				<ul class="text-lg list-none text-left font-mono">
					<li>extern</li>
					<li>false (C23)</li>
					<li>float</li>
					<li>for</li>
					<li>goto</li>
					<li>if</li>
					<li>inline (C99)</li>
					<li>int</li>
					<li>long</li>
					<li>nullptr (C23)</li>
					<li>register</li>
					<li>restrict (C99)</li>
					<li>return</li>
					<li>short</li>
					<li>signed</li>
				</ul>
				<ul class="text-lg list-none text-left font-mono">
					<li>sizeof</li>
					<li>static</li>
					<li>static_assert (C23)</li>
					<li>struct</li>
					<li>switch</li>
					<li>thread_local (C23)</li>
					<li>true (C23)</li>
					<li>typedef</li>
					<li>typeof (C23)</li>
					<li>typeof_unqual (C23)</li>
					<li>union</li>
					<li>unsigned</li>
					<li>void</li>
					<li>volatile</li>
					<li>while</li>
				</ul>
			</div>
		</Slide>
	</Slide>
	<Slide class="h-full place-content-center">
		<Transition visible><h1>Primitive Types 🏷️</h1></Transition>
		<Transition><p class="p-2"><span class="ctype">int</span> - Integer [signed/unsigned, long/short]</p></Transition>
		<Transition><p class="p-2"><span class="ctype">char</span> - Character (1 byte)</p></Transition>
		<Transition
			><p class="p-2"><span class="ctype">float</span> - Single Precision Floating Point Number</p></Transition
		>
		<Transition>
			<p class="p-2"><span class="ctype">double</span> - Double Precision Floating Point Number</p>
		</Transition>
		<Transition>
			<p class="p-2"><span class="ctype">size_t</span> - Return type of the <span class="ctype">sizeof()</span> operator</p>
		</Transition>
		<Transition>
			<p class="p-2"><span class="ctype">void</span> - No value</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center">
		<p class="p-3">Variable Declaration</p>
		<Code lang="c" code="char x;" theme="andromeeda" />
		<p class="p-3">Variable Declaration with Initialization</p>
		<Code lang="c" code="double y = 5.3;" theme="andromeeda" />
		<p class="p-3">Multiple Declarations of the same type</p>
		<Code lang="c" code="int crust, sauce = 2, cheese;" theme="andromeeda" />
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible><h1>Control Statements 🎮</h1></Transition>
		<Transition>
			<h2 class="text-3xl p-3">Conditionals</h2>
				<div class="flex">
					<div class="code-container">
						<Code
						bind:this={code_conditional}
						lang="c"
						theme="andromeeda"
						class="flex-1/2"
						autoIndent={false}
						options={{lineNumbers: true, containerStyle: true}}
						code={`if(x % 6 == 0)
{
	printf("x is divisible by 6.\\n");
}
`}
						/>
					</div>	
				</div>

		<Action do={() => code_conditional.update`if(x % 6 == 0)
{
	printf("x is divisible by 6.\\n");
}
else if(x % 3 == 0)
{
    printf("x is divisible by 3 but not 6.\\n");
}`}
			undo={() => code_conditional.update`if(x % 6 == 0)
{
	printf("x is divisible by 6.\\n");
}
`}
/>

		<Action do={() => code_conditional.update`if(x % 6 == 0)
{
	printf("x is divisible by 6.\\n");
}
else if(x % 3 == 0)
{
    printf("x is divisible by 3 but not 6.\\n");
}
else
{
    printf("x is divisible by neither 3, nor 6.\\n");
}`} 	
		/>
		</Transition>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1>Control Statements 🎮</h1>
		<h2 class="text-3xl p-2">Conditionals</h2>
		<h3 class="text-xl p-2">Switch Statements</h3>
		<div class="code-container">
			<Code
				autoIndent={false}
				theme="andromeeda"
				options={{lineNumbers: true}}
				lang="c"
				code={`int num;
printf("Enter a number between 1 and 3: ");
scanf("%d", &num);
switch(num)
{
    case 1:
        printf("One\\n");
        break;
    case 2:
        printf("Two\\n");
        break;
    case 3:
        printf("Three\\n");
        break;
    default:
        printf("Invalid\\n");
}`}
			/>
		</div>
		<p><a class="text-white text-sm" href="https://youtu.be/fjUG_y5ZaL4" target="_blank">YouTube: Why are Switch Statements So Fast? - Low Level Learning</a></p>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible><h1>Control Statements 🎮</h1></Transition>
		<h2 class="text-3xl p-3">Loops</h2>
		<h3 class="text-xl p-3">While Loop</h3>
		<Code
		 	autoIndent={false}
			theme="andromeeda"
			options={{lineNumbers: true, containerStyle: true}}
			lang="c"
			code={`int answer = 0;
while(answer != 42)
{
    // Annoy the user until they get it right!
    printf("What's the answer to life, the universe, and everything? ");
    scanf("%d", answer);
}`} />
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible><h1>Control Statements 🎮</h1></Transition>
		<h2 class="text-3xl p-3">Loops</h2>
		<h3 class="text-xl p-3">While Loop</h3>
		<img src="images/while_flowchart.png" alt="flowchart showing do-while loop" class="w-sm" />
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Control Statements 🎮</h1>
			<h2 class="text-3xl p-3">Loops</h2>
			<h3 class="text-xl p-3">Do-while Loop</h3>
		</Transition>
		<Code
			lang="c"
			theme="andromeeda" 
			autoIndent={false}
			options={{lineNumbers: true, containerStyle: true}}
			code={`int num;
do
{
    printf("Enter a positive integer: ");
    scanf("%d", &num);
}
while(num <= 0);`}
		/>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Control Statements 🎮</h1>
			<h2 class="text-3xl p-3">Loops</h2>
			<h3 class="text-xl p-3">Do-while Loop</h3>
		</Transition>
		<img src="images/do_while_flowchart.png" alt="flowchart showing do-while loop" class="w-xs" />
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Control Statements 🎮</h1>
			<h2 class="text-3xl p-3">Loops</h2>
		</Transition>
		<img src="images/iteration_meme.jpg" alt="Roadrunner and Coyote, demonstrating difference between do-while and while" />
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible><h1>Control Statements 🎮</h1></Transition>
		<h2 class="text-3xl p-3">Loops</h2>
		<Code
			bind:this={code_loop_example}
		 	autoIndent={false}
			theme="andromeeda"
			options={{lineNumbers: true, containerStyle: true}}
			lang="c"
			code={`int n = 10;
while(n > 1)
{
    printf("%d green bottles hanging on the wall,\\n", n);
    printf("%d green bottles hanging on the wall,\\n", n);
    printf("And if one green bottle should accidentally fall,\\n");
    printf("There'll be %d green bottles hanging on the wall.\\n", n - 1);
    n--;
}`} />

		<Action do={() => code_loop_example.update`for(int n = 10; n > 1; n--)
{
    printf("%d green bottles hanging on the wall,\\n", n);
    printf("%d green bottles hanging on the wall,\\n", n);
    printf("And if one green bottle should accidentally fall,\\n");
    printf("There'll be %d green bottles hanging on the wall.\\n", n - 1);
}`} 
			undo={() => code_loop_example.update`int n = 10;
while(n > 1)
{
    printf("%d green bottles hanging on the wall,\\n", n);
    printf("%d green bottles hanging on the wall,\\n", n);
    printf("And if one green bottle should accidentally fall,\\n");
    printf("There'll be %d green bottles hanging on the wall.\\n", n - 1);
    n--;
}`}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Functions </h1>
		</Transition>
		<Transition>
			<div class="code-container">
				<Code
					lang="c"
					autoIndent={false}
					theme="andromeeda"
					code={`return_type identifier(arg_declarations...)
{
    // body
    return expression;
}`}
				/>
			</div>
		</Transition>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1>Functions </h1>
		<div class="code-container">
			<Code
				lang="c"
				autoIndent={false}
				options={{lineNumbers: true}}
				theme="andromeeda"
				code={`int square(int x)
{
    return x * x;
}`}
				/>
		</div>
		<br><br>
		<Transition>
			<div class="code-container">
				<Code 
					bind:this={code_function}
					lang="c"
					autoIndent={false}
					options={{lineNumbers: true}}
					theme="andromeeda"
					code={`int main(void)
{
    int y = 9;
    int z = square(y); // Capturing return value
    printf("%d\\n", z); // Prints 81
    return 0;
}`}
				/>
			</div>
		</Transition>
		<Action 
			do={() => code_function.update`int main(void)
{
    printf("%d\\n", square(9)); // Prints 81
    return 0;
}`}
			undo={() => code_function.update`int main(void)
{
    int y = 9;
    int z = square(y); // Capturing return value
    printf("%d\\n", z); // Prints 81
    return 0;
}`}

		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Remember Recursion? 🤔</h1>
		</Transition>
		<Transition>
			<p class="p-1.5">How did we recursively define the Fibonacci Sequence?</p>
		</Transition>
		<Transition>
			<p class="p-2 pb-3">{`\\( F_n = F_{n-1} + F_{n-2} \\)`}</p>
		</Transition>
		<Transition>
			<div class="p-3">
				<p class="p-1.5">{`$F_0 = 0$`}</p>
				<p class="p-1.5">{`$F_1 = 1$`}</p>
			</div>
		</Transition>
		<Transition>
			<p>{`$0, 1, 1, 2, 3, 5, 8, 13, 21, \\cdots$`}</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Let's turn it into code.</h1>
			<p class="p-3 w-6xl">Implement a function <code><span class="ctype">int</span> fibonacci(<span class="ctype">int</span> n)</code> that takes n as input and returns the nth Fibonacci number.</p>
		</Transition>
		<Transition>
			<div class="p-2 code-container">
				<Code
					lang="c"
					autoIndent={false}
					theme="andromeeda"
					options={{lineNumbers: true}}
					code={`int fibonacci(int n)
{
    if(n == 0)
        return 0;
    else if(n == 1)
        return 1;
    else
        return fibonacci(n - 1) + fibonacci(n - 2);
}`}
				/>
			</div>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<video type="video/mp4" class="h-[85vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/fibonacci_demo.mp4"></video>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1>Expressions vs Statements</h1>
		<div class="flex justify-around place-content-around w-[70vw]">
			<div class="flex-1 text-2xl p-6">
				<Transition>
					<h3>Expression</h3>
					<p>A piece of code that <b>produces a value</b>, or can be evaluated to get a value.</p>
				</Transition>
				<Transition>
					<div class="code-container">
						<Code class="m-2" lang="c" theme="andromeeda" code="3 + (2 * 4)" />
					</div>
				</Transition>
				<Transition>
					<div class="code-container">
						<Code class="m-2" lang="c" theme="andromeeda" code="age >= 18 && salary > 20000" />
					</div>
				</Transition>
				<Transition>
					<div class="code-container">
						<Code class="m-2" lang="c" theme="andromeeda" code="tea || coffee" />
					</div>
				</Transition>
				<Transition>
					<p>Can appear in any context where a value is allowed.</p>
				</Transition>
			</div>
			<div class="flex-1 text-2xl p-3">
				<Transition>
					<h3>Statement</h3>
					<p>A <b>complete instruction</b> that can be executed.</p>
				</Transition>
				<Transition>
					<div class="code-container">
						<Code class="m-2" lang="c" theme="andromeeda" code="return 10;" />
					</div>
				</Transition>
				<Transition>
					<div class="code-container">
						<Code class="m-2" lang="c" theme="andromeeda" code={`if(isRaining){
    // doSomething
}`} />
					</div>
				</Transition>
				<Transition>
					<div class="code-container">
						<Code class="m-2" lang="c" theme="andromeeda" code={`int numberOfTacos = 0;`} />
					</div>
				</Transition>
				<Transition>
					<p>
						Often separated by semicolon (;) unless they end with a code block.
					</p>
				</Transition>
			</div>
		</div>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<h1>Expressions vs Statements</h1>
		<p>Expressions can also be used as statements.</p>
		<Transition>
			<div class="p-2">An expression followed by a semicolon is called an <span class="underline">expression statement</span>.</div>
			<div class="code-container"><Code class="m-2 w-1/2" lang="c" theme="andromeeda" code={`4 + 5; // Does nothing but valid`} /></div>
			<div class="code-container"><Code class="m-2 w-1/2" lang="c" theme="andromeeda" code={`count++; // Return value ignored`} /></div>
			<div class="code-container"><Code class="m-2 w-1/2" lang="c" theme="andromeeda" code={`printf("Hello World\\n"); // printf returns int`} /></div>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>Assignments</h1>
		<p class="p-2">Assignments are expressions!</p>
		<Transition>
			<p class="p-2">They return a value.</p>
		</Transition>
		<Transition>
			<div class="p-2 code-container">
				<Code bind:this={code_assignment_associativity} lang="c" theme="andromeeda" options={{lineNumbers: true}} code={`int x, y, z;
				x = y = z = 10;`} />
			</div>
		</Transition>
		<Transition>
			<p>Assignments are right-associative.</p>
		</Transition>
		<Action do={()=> code_assignment_associativity.update`int x, y, z;
		x = (y = (z = 10));`}
		undo={() => code_assignment_associativity.update`int x, y, z;
		x = y = z = 10;`} />

		<Action do={()=> code_assignment_associativity.update`int x, y, z;
		x = (y = 10); // z is 10`}
		undo={() => code_assignment_associativity.update`int x, y, z;
		x = (y = (z = 10));`} />

		<Action do={()=> code_assignment_associativity.update`int x, y, z;
		x = 10; // z is 10, y is 10`}
		undo={() => code_assignment_associativity.update`int x, y, z;
		x = (y = 10); // z is 10`} />

		<Action do={()=> code_assignment_associativity.update`int x, y, z;
		10; // z is 10, y is 10, x is 10`}
		undo={() => code_assignment_associativity.update`int x, y, z;
		x = 10; // z is 10, y is 10`} />
		
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>lvalues and rvalues</h1>
		<Transition>
			<p class="p-3">Assignments expressions are of the form <code>lvalue = rvalue</code>.</p>
		</Transition>
		<Transition>
			<p class="p-3">
				Expressions permitted on the left of = are lvalues.<br>
				They represent a place where a value can be stored.
			</p>
		</Transition>
		<Transition>
			<p class="p-3">
				Expressions permitted on the right of = are rvalues. <br>
				Just a value.
			</p>
		</Transition>
		<Transition>
			<p class="p-3">All lvalues are rvalues but not all rvalues are lvalues.</p>
		</Transition>
		<Transition>
			<div class="p-3 code-container">
				<Code lang="c" theme="andromeeda" code={`x = 5; // Valid
				8 = x; // Invalid because 8 is not an lvalue.`} />
			</div>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<img src="https://imgs.xkcd.com/comics/pointers.png" alt="XKCD Comic on Pointers">
		<p class="text-sm my-2">Source: <a href="https://xkcd.com/138/" target="_blank" class="text-white">XKCD</a>, Creative Commons <a class="text-white" target="_blank" href="https://creativecommons.org/licenses/by-nc/2.5/">Attribution-NonCommercial 2.5 License</a></p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Pointers and Indirection 👉</h1>
		</Transition>
		<Transition>
			<p class="m-4 p-3">Pointers store the location of variables in memory.</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30">Every data type has a corresponding pointer type, which can be invoked using the * operator.</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30">A variable directly refers to its value (as an lvalue).</p>
		</Transition>
		<Transition>
			<div class="m-4 px-30 code-container"><Code lang="c" theme="andromeeda" code="int age = 42;"></Code></div>
		</Transition>
		<Transition>
			<p class="m-4 px-30">A pointer does so <strong>indirectly</strong>.</p>
		</Transition>
		<Transition>
			<div class="m-4 px-30 code-container"><Code lang="c" theme="andromeeda" code="int* agePtr = &age;"></Code></div>
		</Transition>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Pointers and Indirection 👉</h1>
		</Transition>
		<Transition>
			<p class="m-4 px-30">We can have pointers to pointers, and pointers to pointers to pointers.</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30">Did we just start counting? 😕</p>
			<div class="code-container">
				<Code lang="c" theme="andromeeda" options={{lineNumbers: true}} code={`int a = 1;
int *x = &a; // pointer to int
int **y = &x; // pointer to pointer to int
int ***z = &y; // pointer to pointer to pointer to int`} />
			</div>
		</Transition>
	</Slide>
	<Slide animate class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Pointers and Indirection 👉</h1>
		</Transition>
		<Transition>
			<p class="m-4 px-30">The value at the location stored in a pointer can be accessed (as an lvalue) by dereferencing it.</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30">Dereference Operator: <span class="text-monospace">*</span></p>
		</Transition>
		<Transition>
			<p class="m-4 px-30"><span class="ccode">NULL</span> (or in C23, <span class="ccode">nullptr</span>) is a special value for a pointer that points to nothing.</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30"> Dereferencing a null pointer is a guaranteed way to get a segfault.</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<video type="video/mp4" class="h-[85vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/pointer_dereference_demo.mp4"></video>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Arrays 🎞️</h1>
		</Transition>
		<Transition>
			<p class="m-4 px-30">Arrays are contiguously stored ordered collections of a type.</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30">They can be stack-allocated or heap-allocated.</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Transition visible>
			<h1>Stack Allocated Arrays 📦</h1>
		</Transition>
		<Transition>
			<p class="m-4 px-30">In order for anything to be allocated on the stack, its size must be known at compile-time (well, kind of).</p>
		</Transition>
		<Transition>
			<p class="m-4 px-30 text-[.7em]">Some C versions support Variable Length Arrays (VLAs), but they're not portable and should be avoided for robust code.</p>
		</Transition>
		<Transition>
			<div class="m-3 px-30 code-container">
				<Code lang="c" theme="andromeeda" code={`// Stack with fixed size
int arr1[100];    // ✅ safe

// VLA (iffy)
int n = 100;
int arr2[n];      // ⚠️ not portable`} />
			</div>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<Code bind:this={code_array_iter} theme="andromeeda" lang="c" options={{lineNumbers: true, autoIndent: false}} code={`#include <stdio.h>
int main(void)
{
    int scores[5] = {92, 86, 93, 39, 80};
    printf("%d\\n", scores[0]); // Prints 92
    printf("%d\\n", scores[1]); // Prints 86
    printf("%d\\n", scores[2]); // Prints 93
    printf("%d\\n", scores[3]); // Prints 39
    printf("%d\\n", scores[4]); // Prints 80
    return 0;
}`} 
		/>
		<Action do={() => code_array_iter.update`#include <stdio.h>
int main(void)
{
    int scores[5] = {92, 86, 93, 39, 80};
    for(int i = 0; i < 5; i++)
    {
        printf("%d\\n", scores[i]);
    }
    return 0;
}`}
			undo={() => code_array_iter.update`#include <stdio.h>
int main(void)
{
    int scores[5] = {92, 86, 93, 39, 80};
    printf("%d\\n", scores[0]); // Prints 92
    printf("%d\\n", scores[1]); // Prints 86
    printf("%d\\n", scores[2]); // Prints 93
    printf("%d\\n", scores[3]); // Prints 39
    printf("%d\\n", scores[4]); // Prints 80
    return 0;
}`}
		/> 
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>Structures 🏢</h1>
		<p class="m-4 px-30">Structures help define our own compound datatypes as combinations of primitive types.</p>
		<p class="m-4 px-30">They are like classes but can only contain member variables and not functions/methods.</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1 class="m-4 px-30">Structures 🏢</h1>
		<Code bind:this={code_structs} lang="c" theme="andromeeda" options={{lineNumbers: true}} code={`#include <stdio.h>
struct Point
{
    int x;
    int y;
};
int main(void)
{
    struct Point position = {1, 3};
    printf("%d\\n", position.x); // Prints 1
    printf("%d\\n", position.y); // Prints 3
    return 0;
}`} 
		/>
		<Action do={() => code_structs.update`#include <stdio.h>
typedef struct Point
{
    int x;
    int y;
}
Point;
int main(void)
{
    Point position = {1, 3};
    printf("%d\\n", position.x); // Prints 1
    printf("%d\\n", position.y); // Prints 3
    return 0;
}`}
		undo={() => code_structs.update`#include <stdio.h>
struct Point
{
    int x;
    int y;
};
int main(void)
{
    struct Point position = {1, 3};
    printf("%d\\n", position.x); // Prints 1
    printf("%d\\n", position.y); // Prints 3
    return 0;
}`}
		/>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>Structures 🏢</h1>
		<video type="video/mp4" class="h-[85vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/structs_demo.mp4"></video>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>Dynamic Memory Allocation</h1>
		<p class="m-4 px-30">Memory on the heap can be allocated using <span class="ccode">malloc()</span>.</p>
		<p class="m-4 px-30">If you also want it initialized to 0, you can use <span class="ccode">calloc()</span>.</p>
		<p class="m-4 px-30">To resize heap-allocated memory, use <span class="ccode">realloc()</span>.</p>
		<br>
		<p class="m-4 px-30">All memory allocated using these functions must be freed using <span class="ccode">free()</span>. Failing to do so produces a memory leak.</p>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<video type="video/mp4" class="h-[85vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/dynamic_array_demo.mp4"></video>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>Dereferencing with Arrays</h1>
		<p class="m-4 px-30">The name of an array resolves to its address.</p>
		<p class="m-4 px-30">Or more precisely, the address of its first element.</p>
		<p class="m-4 px-30"><span class="ccode">array[i]</span> is just syntactical sugar for <span class="ccode">*(array + i)</span>.</p>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Dynamically Allocating 2D Arrays</h1>
		<div class="flex">
			<div class="text-left code-container" style="margin: auto;">
				<Code class="fragment" data-fragment-index="0" lang="c" theme="andromeeda" code={`// Suppose we want N rows and M columns`} />
				<Code class="fragment" data-fragment-index="1" lang="c" theme="andromeeda" code={`int **arr = malloc(N * sizeof(int *));`} />
				<Code class="fragment" data-fragment-index="3" autoIndent={false} lang="c" theme="andromeeda" code={`for(int i = 0; i < N; i++)
{
    arr[i] = malloc(M * sizeof(int));\n}`} 
				/>
			</div>	
			<div>
				{@html `
					<svg width="600" height="460" xmlns="http://www.w3.org/2000/svg">
					<defs>
						<marker id="arrowhead" markerWidth="10" markerHeight="7" refX="10" refY="3.5" orient="auto">
						<polygon points="0 0, 10 3.5, 0 7" fill="white" />
						</marker>
					</defs>

					<style>
						.box { fill: none; stroke: white; stroke-width: 1.5; }
						.label { fill: white; font-family: monospace; font-size: 14px; dominant-baseline: middle; text-anchor: middle; }
						.fragment { opacity: 0; transition: opacity 0.3s; }
						.current-fragment { opacity: 1; }
					</style>

					<!-- arr[i] boxes -->
					<g class="fragment" data-fragment-index="2">
						<rect x="40" y="30" width="100" height="40" class="box" />
						<text x="90" y="50" class="label">arr[0]</text>

						<rect x="40" y="130" width="100" height="40" class="box" />
						<text x="90" y="150" class="label">arr[1]</text>

						<rect x="40" y="230" width="100" height="40" class="box" />
						<text x="90" y="250" class="label">arr[2]</text>

						<rect x="40" y="330" width="100" height="40" class="box" />
						<text x="90" y="350" class="label">arr[3]</text>
					</g>

					<!-- arr[0][j] and arrow -->
					<g class="fragment" data-fragment-index="4">
						<line x1="140" y1="50" x2="230" y2="50" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
						<rect x="250" y="30" width="90" height="40" class="box" />
						<text x="295" y="50" class="label">arr[0][0]</text>
						<rect x="340" y="30" width="90" height="40" class="box" />
						<text x="385" y="50" class="label">arr[0][1]</text>
						<rect x="430" y="30" width="90" height="40" class="box" />
						<text x="475" y="50" class="label">arr[0][2]</text>
					</g>

					<!-- arr[1][j] and arrow -->
					<g class="fragment" data-fragment-index="5">
						<line x1="140" y1="150" x2="230" y2="150" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
						<rect x="250" y="130" width="90" height="40" class="box" />
						<text x="295" y="150" class="label">arr[1][0]</text>
						<rect x="340" y="130" width="90" height="40" class="box" />
						<text x="385" y="150" class="label">arr[1][1]</text>
						<rect x="430" y="130" width="90" height="40" class="box" />
						<text x="475" y="150" class="label">arr[1][2]</text>
					</g>

					<!-- arr[2][j] and arrow -->
					<g class="fragment" data-fragment-index="6">
						<line x1="140" y1="250" x2="230" y2="250" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
						<rect x="250" y="230" width="90" height="40" class="box" />
						<text x="295" y="250" class="label">arr[2][0]</text>
						<rect x="340" y="230" width="90" height="40" class="box" />
						<text x="385" y="250" class="label">arr[2][1]</text>
						<rect x="430" y="230" width="90" height="40" class="box" />
						<text x="475" y="250" class="label">arr[2][2]</text>
					</g>

					<!-- arr[3][j] and arrow -->
					<g class="fragment" data-fragment-index="7">
						<line x1="140" y1="350" x2="230" y2="350" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
						<rect x="250" y="330" width="90" height="40" class="box" />
						<text x="295" y="350" class="label">arr[3][0]</text>
						<rect x="340" y="330" width="90" height="40" class="box" />
						<text x="385" y="350" class="label">arr[3][1]</text>
						<rect x="430" y="330" width="90" height="40" class="box" />
						<text x="475" y="350" class="label">arr[3][2]</text>
					</g>
					</svg>
				`}

			</div>
		</div>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Freeing Dynamically Allocated 2D Arrays</h1>
		<div class="flex">
			<div class="text-left code-container" style="margin: auto;">
				<Code class="fragment" data-fragment-index="0" lang="c" theme="andromeeda" code={`// Free all rows`} />
				<Code class="fragment" data-fragment-index="1" lang="c" theme="andromeeda" code={`for(int i = 0; i < N; i++)`} />
				<Code class="fragment" data-fragment-index="2" lang="c" theme="andromeeda" code={`    free(arr[i]);`} />
				<Code class="fragment" data-fragment-index="4" lang="c" theme="andromeeda" code={`// Finally free the array of pointers`} />
				<Code class="fragment" data-fragment-index="5" lang="c" theme="andromeeda" code={`free(arr);`} />
			</div>

			<div>
				{@html `
				<svg width="600" height="460" xmlns="http://www.w3.org/2000/svg">
				<defs>
					<marker id="arrowhead" markerWidth="10" markerHeight="7" refX="10" refY="3.5" orient="auto">
					<polygon points="0 0, 10 3.5, 0 7" fill="white" />
					</marker>
				</defs>

				<style>
					.box { fill: none; stroke: white; stroke-width: 1.5; }
					.label { fill: white; font-family: monospace; font-size: 14px; dominant-baseline: middle; text-anchor: middle; }
					.crossed { stroke: red; stroke-width: 2; stroke-dasharray: 4 2; }
					.fragment { opacity: 0; transition: opacity 0.3s; }
					.current-fragment { opacity: 1; }
				</style>

				<!-- arr[i] boxes -->
				<g>
					<rect x="40" y="30" width="100" height="40" class="box" />
					<text x="90" y="50" class="label">arr[0]</text>

					<rect x="40" y="130" width="100" height="40" class="box" />
					<text x="90" y="150" class="label">arr[1]</text>

					<rect x="40" y="230" width="100" height="40" class="box" />
					<text x="90" y="250" class="label">arr[2]</text>

					<rect x="40" y="330" width="100" height="40" class="box" />
					<text x="90" y="350" class="label">arr[3]</text>
				</g>

				<!-- arr[i][j] and arrows -->
				<g>
					<line x1="140" y1="50" x2="230" y2="50" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
					<rect x="250" y="30" width="90" height="40" class="box" />
					<text x="295" y="50" class="label">arr[0][0]</text>
					<rect x="340" y="30" width="90" height="40" class="box" />
					<text x="385" y="50" class="label">arr[0][1]</text>
					<rect x="430" y="30" width="90" height="40" class="box" />
					<text x="475" y="50" class="label">arr[0][2]</text>

					<line x1="140" y1="150" x2="230" y2="150" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
					<rect x="250" y="130" width="90" height="40" class="box" />
					<text x="295" y="150" class="label">arr[1][0]</text>
					<rect x="340" y="130" width="90" height="40" class="box" />
					<text x="385" y="150" class="label">arr[1][1]</text>
					<rect x="430" y="130" width="90" height="40" class="box" />
					<text x="475" y="150" class="label">arr[1][2]</text>

					<line x1="140" y1="250" x2="230" y2="250" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
					<rect x="250" y="230" width="90" height="40" class="box" />
					<text x="295" y="250" class="label">arr[2][0]</text>
					<rect x="340" y="230" width="90" height="40" class="box" />
					<text x="385" y="250" class="label">arr[2][1]</text>
					<rect x="430" y="230" width="90" height="40" class="box" />
					<text x="475" y="250" class="label">arr[2][2]</text>

					<line x1="140" y1="350" x2="230" y2="350" stroke="white" stroke-width="2" marker-end="url(#arrowhead)" />
					<rect x="250" y="330" width="90" height="40" class="box" />
					<text x="295" y="350" class="label">arr[3][0]</text>
					<rect x="340" y="330" width="90" height="40" class="box" />
					<text x="385" y="350" class="label">arr[3][1]</text>
					<rect x="430" y="330" width="90" height="40" class="box" />
					<text x="475" y="350" class="label">arr[3][2]</text>
				</g>

				<!-- Cross out inner arrays on fragment 3 -->
				<g class="fragment" data-fragment-index="3">
					<line x1="250" y1="30" x2="520" y2="70" class="crossed"/>
					<line x1="250" y1="130" x2="520" y2="170" class="crossed"/>
					<line x1="250" y1="230" x2="520" y2="270" class="crossed"/>
					<line x1="250" y1="330" x2="520" y2="370" class="crossed"/>
				</g>

				<!-- Cross out arr[] on fragment 6 -->
				<g class="fragment" data-fragment-index="6">
					<line x1="40" y1="30" x2="140" y2="70" class="crossed"/>
					<line x1="40" y1="130" x2="140" y2="170" class="crossed"/>
					<line x1="40" y1="230" x2="140" y2="270" class="crossed"/>
					<line x1="40" y1="330" x2="140" y2="370" class="crossed"/>
				</g>
				</svg>
				`}
			</div>
		</div>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1 class="p-3">Strings</h1>
		<Transition>
			<p class="mx-6 my-4">C does not (really) have a built-in string data type.</p>
		</Transition>
		<Transition>
			<p class="mx-6 my-4">Instead, we have arrays of characters.</p>
		</Transition>
		<Transition>
			<p class="mx-6 my-4">Strings in C are just character arrays that end with the null terminator.</p>
		</Transition>
		<Transition>
			<div class="code-container"><Code lang="c" theme="andromeeda" code={`char myString[] = "Texas";`} /></div>
		</Transition>
		<Transition>
			<div class="code-container"><Code lang="c" theme="andromeeda" code={`char myString[] = {'T', 'e', 'x', 'a', 's', '\\0'};`} /></div>
		</Transition>
		<Transition>
			<p class="mx-6 my-4"><span class="ccode">printf</span> with <span class="ccode">%s</span> and other string functions stop when they see '\0'.</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1 class="p-3">What data type is this? 🤔</h1>
		<p class="mx-6 my-9 ccode">char *var[6];</p>
		<Transition>
			<p class="mx-6 my-9">It's an array of pointers!</p>
		</Transition>
		<Transition class="flex">
			<div class="code-container">
				<Code lang="c" theme="andromeeda" autoIndent={false} code={`char *cities[] = {"Arlington", "Dallas", "Fort Worth", "Dalworthington Gardens", "Pantego"};
printf("%s\\n", cities[1]); // Prints Dallas
printf("%s\\n", cities[2]); // Prints Fort Worth`} />
			</div>
		</Transition>
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center">
		<h1 class="p-3">Passing Pointer Arrays</h1>
		<Code bind:this={code_ptrarray} lang="c" theme="andromeeda" options={{lineNumbers: true}} code={`#include <stdio.h>

void printCities(char *cities[], int numberOfCities)
{
    for(int i = 0; i < numberOfCities; i++)
    {
        printf("%s\\n", cities[i]);
    }
}

int main(void)
{
    char *myCities[] = {"Arlington", "Dallas", "Fort Worth", "Dalworthington Gardens", "Pantego"};
    printCities(myCities, 6);
    return 0;
}`} />

		<Action do={() => code_ptrarray.update`#include <stdio.h>

void printCities(char *cities[])
{
    for(int i = 0; cities[i][0] != '\\0'; i++)
    {
        printf("%s\\n", cities[i]);
    }
}

int main(void)
{
    char *myCities[] = {"Arlington", "Dallas", "Fort Worth", "Dalworthington Gardens", "Pantego", ""};
    printCities(myCities);
    return 0;
}`} 

			undo = {() => code_ptrarray.update`#include <stdio.h>

void printCities(char *cities[], int numberOfCities)
{
    for(int i = 0; i < numberOfCities; i++)
    {
        printf("%s\\n", cities[i]);
    }
}

int main(void)
{
    char *myCities[] = {"Arlington", "Dallas", "Fort Worth", "Dalworthington Gardens", "Pantego"};
    printCities(myCities, 6);
    return 0;
}`} />
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Command-Line Arguments</h1>
		<p class="mx-6 my-9">Command-Line Arguments are passed to the main function as a pointer array.</p>
		<p class="mx-6 my-9">To use command-line arguments, use this signature for the main function</p>
		<Code lang="c" theme="andromeeda" code={`int main(int argc, char *argv[])`} />
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Command-Line Arguments</h1>
		<img src="images/commandline_args.png" alt="Command Line Arguments in C Demo" class="w-auto h-[80vh]">
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>UNIX Review and Debugging</h1>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Shell Commands</h1>
		<div class="grid grid-cols-[auto_auto] gap-x-16 gap-y-4 font-mono text-2xl mt-8 text-left">
			<Transition><div>ls</div></Transition>
			<Transition><div>list files/directories</div></Transition>

			<Transition><div>mkdir</div></Transition>
			<Transition><div>create a new directory</div></Transition>

			<Transition><div>cd</div></Transition>
			<Transition><div>change to the named directory</div></Transition>

			<Transition><div>cat</div></Transition>
			<Transition><div>print contents of file all at once</div></Transition>

			<Transition><div>cp</div></Transition>
			<Transition><div>copy a file</div></Transition>

			<Transition><div>mv</div></Transition>
			<Transition><div>move/rename a file</div></Transition>

			<Transition><div>rm</div></Transition>
			<Transition><div>delete a file</div></Transition>

			<Transition><div>more</div></Transition>
			<Transition><div>print file contents in pages</div></Transition>

			<Transition><div>pwd</div></Transition>
			<Transition><div>print the current path</div></Transition>
		</div>
	</Slide>
	<Slide class="h-full place-items-center place-content-center-safe">
		<h1>Redirection</h1>
		<Transition>
			<p class="ccode p-3">command &gt; output_file.txt</p>
		</Transition>
		<Transition>
			<p class="ccode p-3">command &lt; input_file.txt</p>
		</Transition>
		<Transition>
			<p class="ccode p-3">command &lt; input_file.txt &gt; output_file.txt</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Redirection: Output Demo</h1>
		<video type="video/mp4" class="h-[83vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/output_redirection_demo.mp4"></video>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Redirection: Input Demo</h1>
		<video type="video/mp4" class="h-[83vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/input_redirection_demo.mp4"></video>
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center text-left">
		<h1>Matching Expected Outputs and Diff</h1>
		<ul class="m-3 w-4xl">
			<Transition>
				<li class="m-4 py-3">Sometimes, you need your program&CloseCurlyQuote;s behavior to exactly match a given format.</li>
			</Transition>
			<Transition>
				<li class="m-4 py-3">Often, your programs will be run by other programs, rather than humans.</li>
			</Transition>
			<Transition>
				<li class="m-4 py-3">Humans can easily process slight differences in output. Computers? Not so much.</li>
			</Transition>
		</ul>
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center text-left">
		<h1>Matching Expected Outputs and Diff</h1>
		<h2 class="text-4xl m-3">Say we want to print a 2D array.</h2>
		<div class="flex m-3">
			<div style="font-family: 'Consolas';" class="code-container">
				Example output:<br>
				<pre>
-------------------------
|  2|  4|  5|  6|  7|  9|
| 10|-23|  4|  5|  2|  7|
|  0|  3| 10| 33|234| 40|
-------------------------
				</pre>
			</div>
			<div class="code-container">
				<Code lang="c" theme="andromeeda" code={`// Your program got this array as the answer.

int myArray[3][6] = {{2, 4, 5, 6, 7, 9},
                    {10, -23, 4, 5, 2, 7},
                    {0, 3, 10, 33, 234, 40}};

print_array(myArray, 3, 6);
`}></Code>
			</div>
		</div>
		<p class="text-xl w-[60vw] text-center">Implement <span class="ccode"><span class="ctype">void</span> print_array(<span class="ctype">int</span>* arr[], <span class="ctype">int</span> rows, <span class="ctype">int</span> cols)</span> using this output format.</p>
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center">
		<h1 class="mb-6">Matching Expected Outputs and Diff</h1>
		<div class="text-left w-[75vw]">
			<p class="mx-6 my-9">Checking that we did it right!</p>
			<p class="mx-6 my-9">The <span class="ccode">diff</span> command takes two files and tells if they are identical, and optionally tells where they differ, if they do.</p>
			<p class="ccode mx-6 my-9">$ diff file1 file2</p>
			<p class="ccode mx-6 my-9">$ diff your_output.txt expected_output.txt</p>
		</div>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1 class="mb-6">GDB Commands</h1>
		<table class="text-xl font-light" style="table-layout: fixed;">
			<tbody>
				<tr>
					<td><span class="shortcut">b</span>reak</td>
					<td><Transition>Set a breakpoint</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">p</span>rint</td>
					<td><Transition>Print the value of a variable/expression</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">n</span>ext</td>
					<td><Transition>Execute next line (step over if function)</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">s</span>tep</td>
					<td><Transition>Execute next line (step into if function)</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">r</span>un</td>
					<td><Transition>Start execution of the program</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">c</span>ontinue</td>
					<td><Transition>Continue execution until next breakpoint/end of program</Transition></td>
				</tr>
				<tr>
					<td>watch</td>
					<td><Transition>Break when a variable/expression changes value</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">l</span>ist</td>
					<td><Transition>Display source code</Transition></td>
				</tr>
				<tr>
					<td><span class="shortcut">q</span>uit</td>
					<td><Transition>Exit out of GDB</Transition></td>
				</tr>
			</tbody>
			
		</table>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Reverse Debugging</h1>
		<video type="video/mp4" class="h-[85vh]" controls muted  src="https://github.com/aryan-02/c-review-slides/releases/download/v1.0/reverse_debugging_demo.mp4"></video>
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center">
		<h1>Common Errors</h1>
		<Code lang="c" theme="andromeeda" code={`int some_function()
{
    if(some_error_condition)
        return NULL;  // ❌ Wrong: NULL is for pointers
}`} />
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center">
		<h1>Common Errors</h1>
		<Code lang="c" theme="andromeeda" code={`int* foo() 
{
    int x = 42;
    return &x;  // ❌ Address is invalid after function returns
}`} />
	</Slide>
	<Slide animate class="h-full place-items-center place-content-center">
		<h1>Common Errors</h1>
		<Code lang="c" theme="andromeeda" code={`int arr[3];
arr[3] = 0; // ❌ Index is out of range`} />
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Good Coding Practices</h1>
		<Transition>
			<p class="m-4 py-3">Indent your code properly.</p>
		</Transition>
		<Transition>
			<p class="m-4 py-3">Use meaningful variable names.</p>
		</Transition>
		<Transition>
			<p class="m-4 py-3">Avoid using magic numbers.</p>
		</Transition>
		<Transition>
			<p class="m-4 py-3">Initialize your variables to avoid undefined behavior.</p>
		</Transition>
		<Transition>
			<p class="m-4 py-3">Try to make your code self-documenting, but comment when appropriate.</p>
		</Transition>
		<Transition>
			<p class="m-4 py-3">Try to limit functions to small tasks.</p>
		</Transition>
	</Slide>
	<Slide class="h-full place-content-center place-items-center">
		<h1>Good Coding Practices</h1>
		<img src="https://imgs.xkcd.com/comics/good_code.png" alt="XKCD: Good Code">
		<p class="text-sm my-2">Source: <a href="https://xkcd.com/844" target="_blank" class="text-white">XKCD</a>, Creative Commons <a class="text-white" target="_blank" href="https://creativecommons.org/licenses/by-nc/2.5/">Attribution-NonCommercial 2.5 License</a></p>
	</Slide>
	<Slide class="h-full place-items-center place-content-center">
		<h1>Topics Not Covered Here</h1>
		<ul class="m-3 w-4xl text-left">
			<li class="m-4 py-3">Strings and the string.h library</li>
			<li class="m-4 py-3">File Handling</li>
			<li class="m-4 py-3">Bit Manipulation and Bitmasking</li>
			<li class="m-4 py-3">const</li>
		</ul>
	</Slide>
</Presentation>


<style>
	p {
		font-family: 'Montserrat', 'Helvetica', sans-serif;
	}
	h1 {
		margin-bottom: 3rem;
	}
	h1,
	h2,
	h3,
	h4,
	h5 {
		font-family: 'Montserrat', 'Helvetica', sans-serif;
		font-weight: 300;
	}
	.raw-bullet {
		margin: 2rem 0;
	}
	.ccode{
		font-family:  'Monospace Neon', 'Roboto Mono', 'Consolas', monospace;
	}
	.ctype {
		font-family: 'Monospace Neon', 'Roboto Mono', 'Consolas', monospace;
		color: rgb(199, 77, 237);
	}
	.code-container {
		margin: 0;
		padding: 0;
		box-shadow: none;
		background: transparent;
		border: none;
	}
	.shortcut {
		font-weight: bold;
		text-decoration: underline;
	}
	table td:nth-child(2) {
		width: 35vw;
	}
	td {
		height: 3em;
	}

</style>
