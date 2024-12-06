# Noise-removing-by-Fourier-transform-
recObj = audiorecorder(44100, 16, 1);
disp('Recording...');
recordblocking(recObj, 5);
disp('End of recording.');
original_sound = getaudiodata(recObj);
[b, a] = butter(4, 0.2, 'low'); 
filtered_sound = filter(b, a, original_sound);
sound(original_sound, 44100);
pause(7);

sound(filtered_sound, 44100);
figure;
subplot(2,1,1);
plot(original_sound);
title('Original Sound');
subplot(2,1,2);
plot(filtered_sound);
title('Filtered Sound');


figure;
subplot(2,1,1);
plot(abs(fft(original_sound)));
title('FFT of Original Sound');
subplot(2,1,2);
plot(abs(fft(filtered_sound)));
title('FFT of Filtered Sound');
