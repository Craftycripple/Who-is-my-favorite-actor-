# Who is my FAVORITE actor?
Построение VGG подобной сверточной модели для мультиклассового предсказания.

**Цель данного минипроекта** — применить навыки, полученные на видеокурсе по основам приложения PyTorch, и построить модель, которая предсказывает одного из моих 3-х любимых актеров (*Крис Хэмсфорт*, *Джеймс Макэвой*, *Мэттью МакКонахи*).

Так как проект, в основном, учебный, использовались довольно базовые и упрощенные подходы. По этому поводу несколько заметок:
1. Было решено взять метрику **Accuracy** для простоты. Однако, в такой задаче (_multiclass classification_) явно будет разумнее взять такие метрики, как **Precision**, **Recall** и **F1-score** (+ можно было выгрузить метрики из **torchmetrics**).
2. Использовалась кастомная модель _VGG-16_ с использованием BatchNorm слоев. Понятно, что можно было попробовать более продвинутые алгоритмы (типа Resnet и т.п.), и они, скорее всего, дали бы более хороший результат. Но, повторюсь, задача проекта — научиться (более-менее) строить процесс от начала до конца, поэтому было решено взять самую простую модель.
3. Так как в наличие было только GPU от Google Collab, количество эпох равно 300 (проверял модель и на 100, и на 200 эпох. Результаты чуть хуже). В идеале, можно было еще попробовать поиграться с количеством эпох, а также протестировать другой оптимизатор (допустим, Adam).
4. Картинки были заранее отфильтрованы: 1) в наборы не были добавлены фото, где актер с группой людей, 2) актер вдали на фоне, 3) кадр "слишком" со стороны, 4) ошибочные фото (допустим, по запросу "_James McAvoy_" гугл выдавал пару фото _Хью Джекмана_; это я тоже удалял). Однако, в наборе могут быть повторяющиеся, или очень похожие картинки, что, предположительно, может склонить модель к переобучению.
5. В идеале, можно было улучшить процесс аугментации (+ использовать сторонную библиотеку, типа **Albumentation**). Однако, как и упоминалось, задачой не стояло получение наилучшей оценки, в связи с чем были осуществлены более простые подходы.

Ссылка на видеокурс: https://www.youtube.com/watch?v=Z_ikDlimN6A
