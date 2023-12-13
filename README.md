# Quantum-True-Random-Number-Generator - (QRNG) #
## Solve pseudo-randomness utilizing Quantum Superposition. ##

This project is written on Q# language and have the foundation from Azure tutorial named, "Create your first Q# program by using the Quantum Development Kit". 

### What is pseudo randomness? ###
Classical computer based Software-generated random numbers only are pseudorandom. They are not truly random because the computer uses an algorithm based on a distribution, and are not secure because they rely on deterministic, predictable algorithms. A pseudorandom number generator generates a deterministic sequence of numbers based on some initial value, called a seed. To better approximate random values, this seed is often the current time from the CPU's clock.

### Quantum Random Number Generation (QRNG) ###
QRNG generates random numbers with a high source of entropy using unique properties of quantum physics. This relies on the intrinsic randomness of quantum mechanics to produce true random numbers. By putting a qbit into quantum superposition and mesuring the qubit, we can strat with a trule random position. 

### How it works? ###

You start by taking a qubit in a basis state, for example zero. The first step of the QRNG is to use an H operation to put the qubit into an equal superposition. The measurement of this state results in a zero or a one with 50% probability of each outcome. The value of this bit is truly random, there's no way of knowing what you will get after the measurement. But how can you use this behavior to generate larger numbers to use as a valid password?

   - Let's say you repeat the process four times, generating this sequence of binary digits:
     
    ``` 0,0,1,0,1,1,0,1 ```

  - If you concatenate, or combine, these bits into a bit string, you can form a larger number. In this example, the bit sequence is equivalent to 45 in decimal.
    
    ``` 00101101 = 45 ```

    ## ##

### Prerequisites ###

    .NET Core 6.0
    Visual Studio Code
    Microsoft Quantum Development Kit (QDK) for VS Code



### Required libraries ###

Standard Libraries

    ```Microsoft.Quantum.Canon;
       Microsoft.Quantum.Intrinsic;
       Microsoft.Quantum.Measurement; ``` 
       
For the complete random number generator, you need to include two other libraries: ```Microsoft.Quantum.Math``` and ```Microsoft.Quantum.Convert```.

## Code Brakedown ##
 Allocating a qubit.
 
 ```  use q = Qubit();  ```
 
 Put the qubit in to quntum superposition.
 
  ``` H(q); ```
  
 Measuring the value of the qubit.
 
  ``` return M(q);  ```

### Genarating the number ###
By mesuring the value of the Qbit in quantum superposition, we can have a truely random starting point. We can utalize a classical for loop to genarate the number within given parameters.

 ``` SampleRandomNumberInRange``` operation uses a for loop to genarate large complex numbers.


### Setting min & max ###

    The ``` SampleRandomNumberInRange ```
     operation now takes two parameters:
     "min" and "max".

    The repeat loop continues until the generated output is within the specified range 
    "min" to "max".

    The ```SampleRandomNumber``` entry point sets both the minimum "min" and maximum "max" values.

Now, when you call ```SampleRandomNumber()```, it will generate a random number within the specified range [min, max]. Adjust the values of min and max accordingly based on your requirements.


[Microsoft Documentation](https://learn.microsoft.com/en-us/training/modules/qsharp-create-first-quantum-development-kit/)
