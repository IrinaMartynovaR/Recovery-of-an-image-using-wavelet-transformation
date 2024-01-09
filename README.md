# Recovery-of-an-image-using-wavelet-transformation
# Вейвлет-восстановление изображения с удаленными линиями и текстом

## 1. Постановка задачи

Под изображением понимается вектор $f\in \mathbf{R}^s$. Задача заключается в восстановлении неизвестного изображения $u\in \mathbf{R}^s$ по наблюдаемому изображению $f$. 

Для восстановления используется алгоритм, описанный в статье [1], основанный на вейвлет-преобразовании и минимизации функционала.

## 2. Литература

1. J.F. Cai, R.H. Chan, and Z. Shen,A framelet-based image inpainting algorithm, Applied and Computational Harmonic Analysis24(2008), no. 2, 131–149.

## 3. Реализация

Для решения задачи вейвлет-восстановления используется класс `CWaveletAnalis`, включающий в себя методы для вейвлет-разложения и восстановления изображения.

Пример использования алгоритма на случайном изображении и изображении с удаленным текстом представлен в разделе 3.

## 4. Пример использования

```python
# Пример использования на случайном изображении
I = np.random.normal(1, 1, size=(17, 15))
wa = CWaveletAnalis(I, 3)
J = wa.Reconstruction_I(wa.W)
print(np.max(np.abs(I - J)))

# Пример использования на изображении с удаленным текстом
f = Image.open('im6.jpeg').convert('L')
# ... (пропущен код для обработки изображения) ...

# Вейвлет-восстановление и вывод результата
j = 3
wa = CWaveletAnalis(Pf, j)
WPf = wa.W 
beta = wa.W
lamb = np.zeros(WPf.shape) + 1
u_star, beta = optim(wa, beta, 1000, lamb)

fig = plt.figure(figsize=(5, 5))
plt.imshow(u_star, cmap='gray')
