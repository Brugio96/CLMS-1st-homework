# Iteresting results

MFCC  ZCR  SC
42 features

y=audio,sr=fs,n_fft=2048,hop_length=512,window='hamming',n_mels=40,fmin=80,fmax=8000, n_mfcc=n_mfcc,norm='ortho')

<pre>
Normalized confusion matrix
[[1.         0.         0.        ]
 [0.20769231 0.79230769 0.        ]
 [0.         0.         1.        ]]
 </pre>
The accuracy is 0.9691075514874142


----------------------------------------------------------------------------
pyAudioAnalysis
136 -> 42 features selected via k-best
<pre>
Normalized confusion matrix
[[1.         0.         0.        ]
 [0.         0.83076923 0.16923077]
 [0.         0.03084833 0.96915167]]
</pre>
 0.9610983981693364
 
 
----------------------------------------------------------------------------
MFCC  ZCR  SC
42 features -> 2 features

feature selected are 1st and  3rd mfcc components

<pre>
Normalized confusion matrix
[[0.96901408 0.02816901 0.0028169 ]
 [0.27692308 0.72307692 0.        ]
 [0.         0.         1.        ]]
 </pre>
 The accuracy is 0.9462242562929062
 
 Instead selecting 2 features via k best attinging pyAudioDataset produce result that are not interesting
 
 
Increasing number of feature, progressively add:
<pre>
1 3 2 4 6 zcr sc
---------
  mfcc
</pre>

 
----------------------------------------------------------------------------
### Effect of balancing dataset

using: 2 feature from pyAudioAnalysis [ 1 65]

##### unbalanced dataset
Normalized confusion matrix
<pre>
[[0.96901408 0.         0.03098592]
 [0.04615385 0.         0.95384615]
 [0.01799486 0.         0.98200514]]
</pre>
 The accuracy is 0.8306636155606407
 
 
##### balanced dataset
Normalized confusion matrix
<pre>
[[0.91780822 0.07671233 0.00547945]
 [0.00258398 0.6124031  0.38501292]
 [0.00268817 0.25806452 0.73924731]]
</pre>
The accuracy is 0.75355871886121

----------------------------------------------------------------------------
### Effect of normalizing dataset
<pre>
audio = audio / np.abs(audio).max()
audio = scale.minmax_scale(audio,feature_range=(-1,1),axis=0)
</pre>
By applying one of the two expression above result get worse
