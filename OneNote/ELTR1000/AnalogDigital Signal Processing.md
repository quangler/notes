**Modulation:** the process of varying one or more parameters of a carrier signal according to the values of the message signal. (think binary on and off for data)

  

**Pulse Code Modulation:** digital modulation technique - turns it into 1s and 0s (resembles binary)

**Analog Modulation**: (Amplitude Modulation (AM), Frequency Modulation (FM), Phase Modulation (M))

  

Basic Elements of PCM (pulse code modulation):

**(transmitter)**

**Low Pass Filter:** a filter to eliminate high frequency components in input analog signal which is greater than the highest frequency of message signal. (done to avoid aliasing)

  

**Sampler:** the process of measuring the values of continuous-time signal in a discrete form

  

**Quanitzer:** process of reducing the excessive bits and confining the data from analog to digital

- Rounds the sampled data to an approximate/near stabilized value

  

**Encoder**: the actual digitization of analog signal.

- Designates each quantized level by a binary code
- Sample-and-hold process
- LPF, Sampler, and Quantizer will act as an analog to digital converter

  

**Both sampling and quantization loses information -** difference of input and output value is called **quantization error**

  

**Companding**: mixture of compressing and expanding

- Non-linear technique used in PCM which compresses the data at the transmitter and expands the same data at the receiver
- Noise and crosstalk are reduced by using this technique

  
  

**(receiver)**

**Regenerative Repeater Circuit**: increases signal strength

- Output of the channel also has one regenerative repeater circuit to compensate signal loss and reconstruct signal / increase its strength

  

**Decoder:** decodes the pulse coded waveform to reproduce original signal - circuit acts as the demodulator

  

**Reconstruction Filter**: after digital-to-analog conversion (done by regenerative circuit and decoder) a low pass filter is employed, called a reconstruction filter to get back to the original signal