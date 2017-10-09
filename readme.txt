This is part of a larger project done for Brandeis University class COSI 177 in Spring, 2016 that focused on using signal 
processing in order to find and report statistics on groups of songs.

This is an implementation in MATLAB of the Maximum Key Correlation algorithm described in "Musical Key Extraction from Audio,"
Steffen Pauws. 

The algorithm is divided up into ten different scripts. Here is a brief overview of the algorithm.

getkey.m: This is the master function. It reads in a wav file and reports the key as an integer, 1-24. Note that in Western
music there are actually only 12 key signatures. This algorithm is designed to indicate whether a minor or major key is
being used as well.

getFreqsAmps.m: This function returns a matrix of frequencies and their respective amplitudes within the span of 4 octaves.

getAbsPitches.m: This function takes in a maxtrix of frequencies and amplitudes and matches it to pitches in western music.
It then weighs each pitch.

From here there are 2 approaches to take. 

1) We can try to determine the tonic and modality with the strongest weighted pitch and looking at the minor third and major
third. This method uses the determineTonic and determineTonality.

2) We can rank each pitch instead of using the absolute amplitudes. This ranks all the key signatures that are most likely
and then picks the max.

These methods both leave something to be desired in terms of accuracy, but I have ideas on how to improve.

1) Change range of pitches. Having a range that is too large may mean that ambient noises skew the results. A narrow band of 
pitches may not provide enough data.

2) Looking only at the strongest pitch is not the best way to identify a key. For example if a song is in the key of G major,
several notes could dominate that could also idicate other keys such as C or D. Looking at each note and the respective third,
fifth, and seventh intervals could improve the algorithm's guess.
