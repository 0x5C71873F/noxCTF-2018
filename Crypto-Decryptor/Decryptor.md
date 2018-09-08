# Challenge Name : Decryptor
>
>I created this nice decryptor for RSA ciphertexts, you should try it out!
>
>nc chal.noxale.com 4242
>
>Oh, and someone told me to give this to you: 
>N = 140165355674296399459239442258630641339281917770736077969396713192714338090714726890918178888723629353043167144351074222216025145349467583141291274172356560132771690830020353668100494447956043734613525952945037667879068512918232837185005693504551982611886445611514773529698595162274883360353962852882911457919 
>c = 86445915530920147553767348020686132564453377048106098831426077547738998373682256014690928256854752252580894971618956714013602556152722531577337080534714463052378206442086672725486411296963581166836329721403101091377505869510101752378162287172126836920825099014089297075416142603776647872962582390687281063434 
>e = 65537


The Decryptor service is programmed to decrypt any ciphertext except the one we have . So we have to represent the ciphertext in some other way such that it decrypts to a plaintext which is related to the original plaintext. In Cryptography, this property of a cipher is known as Malleability . RSA with a proper padding is not malleable while the naked RSA used here is.


## The Math

The RSA Encryption is given by 

![e1](https://latex.codecogs.com/gif.latex?c%3Dm%5E%7Be%7D%5C%2Cmod%5C%2CN)

where,  
![c](https://latex.codecogs.com/gif.latex?c) is ciphertext  
![m](https://latex.codecogs.com/gif.latex?m) is plaintext  
![e](https://latex.codecogs.com/gif.latex?e) is public exponent  
![N](https://latex.codecogs.com/gif.latex?N) is modulus

Suppose we take a random integer ![S](https://latex.codecogs.com/gif.latex?S) , We multiply ![SN](https://latex.codecogs.com/gif.latex?S%5E%7Be%7D%5C%2Cmod%5C%2CN) on both sides

![eq1](https://latex.codecogs.com/gif.latex?c%5Ccdot%20%5Cleft%20%28%20S%5E%7Be%7D%5C%2Cmod%5C%2CN%20%5Cright%20%29%3D%5Cleft%20%28%20m%5E%7Be%7D%5C%2Cmod%5C%2CN%20%5Cright%20%29%5Ccdot%20%5Cleft%20%28%20S%5E%7Be%7D%5C%2Cmod%5C%2CN%20%5Cright%20%29)

![eq2](https://latex.codecogs.com/gif.latex?c%5Ccdot%20%5Cleft%20%28%20S%5E%7Be%7D%5C%2Cmod%5C%2CN%20%5Cright%20%29%3D%5Cleft%20%28%20m%5Ccdot%20S%20%5Cright%20%29%5E%7Be%7D%5C%2Cmod%5C%2CN)

Decrypting the LHS part of the equation with decryptor gives us ![eq3](https://latex.codecogs.com/gif.latex?%5Cleft%20%28%20m%5Ccdot%20S%20%5Cright%20%29) , using which ![m](https://latex.codecogs.com/gif.latex?m) is trivial to get.

Now that we know what to do, we can write a simple python script decryptor.py which can do all the above.

Aaaaaand we get the flag.

## Flag

`noxCTF{0u7sm4r73d}`
