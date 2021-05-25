# Lambda Library
\ - обозначение для лямбда

## 14 лекция
<p>
    <table>
        <tr>
            <td width="200px">Нумералы Чёрча</td>
            <td>0 = \ x y. y</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>1 = \ x y. x y</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>2 = \ x y. x(x y)</td>
        </tr>
        <tr>
            <td width="200px">Увеличение на 1</td>
            <td>succ = \ n x y. x(n x y)</td>
        </tr>
        <tr>
            <td width="200px">Сложение (m+n)</td>
            <td>plus = \ m n. m succ n</td>
        </tr>
        <tr>
            <td width="200px">Умножение (m*n)</td>
            <td>mul = \m n. m(plus n)</td>
        </tr>
        <tr>
            <td width="200px">Возведение в степень (m^n)</td>
            <td>exp = \m n x y. n m x y</td>
        </tr>
        <tr>
            <td width="200px"><i>true</td>
            <td>true = \ x y. x</td>
        </tr>
        <tr>
            <td width="200px"><i>false</td>
            <td>false = \ x y. y</td>
        </tr>
        <tr>
            <td width="200px">if <i>c</i> then <i>x</i> else <i>y</td>
            <td>if = \ c x y. c x y</td>
        </tr>
        <tr>
            <td width="200px">Логическое "И"</td>
            <td>and = \ x y. if x y false = \xy. x y false</td>
        </tr>
        <tr>
            <td width="200px">Логическое "ИЛИ"</td>
            <td>or = \ x y. if x true y = \ x y. x true y</td>
        </tr>
        <tr>
            <td width="200px">Проверка на ноль</td>
            <td>isZero = \ n. n(\ y. false) true</td>
        </tr>
        <tr>
            <td width="200px">Конструктор пары</td>
            <td>pair = \ x y f. f x y</td>
        </tr>
        <tr>
            <td width="200px">Получение первого компонента пары</td>
            <td>first = \ p. p true</td>
        </tr>
        <tr>
            <td width="200px">Получение второго компонента пары</td>
            <td>second = \p. p false</td>
        </tr>
        <tr>
            <td width="200px">Уменьшение на 1</td>
            <td>pre = \ n x y. second (n (g x) (pair y y))</td>
        </tr>
        <tr>
            <td width="200px">Вычитание</td>
            <td>sub = \ m n. m pre n</td>
        </tr>
        <tr>
            <td width="200px">Факториал</td>
            <td>fact = \ n. (isZero n) 1 (mult n(fact (pre n)))</td>
        </tr>
        <tr>
            <td width="200px">Парадоксальный оператор Карри</td>
            <td>Y = \ f. (\ x. f(x x))(\ x. f(x x))</td>
        </tr>
    </table>
</p>

## 7 семинар
<p>
    <table>
        <tr>
            <td width="200px">Отрицание</td>
            <td>not = \ b. if b false true</td>
        </tr>
        <tr>
            <td width="200px">Меньше или равно</td>
            <td>"<=" = \ n m. isZero (sub n m)</td>
        </tr>
        <tr>
            <td width="200px">Больше или равно</td>
            <td>">=" = \ n m. "<=" m n</td>
        </tr>
        <tr>
            <td width="200px">Меньше</td>
            <td>"<" = \ n m. not (">=" n m)</td>
        </tr>
        <tr>
            <td width="200px">Больше</td>
            <td>">" = \ n m. not ("<=" n m)</td>
        </tr>
        <tr>
            <td width="200px">Остаток от деления</td>
            <td>mod = \ n m. if ("<" n m) n (mod (sub n m) m)</td>
        </tr>
        <tr>
            <td width="200px">Наибольший общий делитель</td>
            <td>gcd = \ a b. if (isZero b) a (gcd b (mod a b))</td>
        </tr>
        <tr>
            <td width="200px">Равенство</td>
            <td>"=" = \ n m. if ( ("<=" n m) and (">=" n m))</td>
        </tr>
        <tr>
            <td width="200px">Пустой список</td>
            <td>empty = \ f x. x</td>
        </tr>
        <tr>
            <td width="200px">Список</td>
            <td>list = \ h t f x. f h (t f x)</td>
        </tr>
        <tr>
            <td width="200px">Сумма списка</td>
            <td>sum = \ l. l plus 0</td>
        </tr>
        <tr>
            <td width="200px">Проверка на пустоту списка</td>
            <td>isEmpty = \ l. l</td>
        </tr>
        <tr>
            <td width="200px">Извлечение головы списка</td>
            <td>head = \ l. l true empty</td>
        </tr>
        <tr>
            <td width="200px">Извлечение хвоста списка</td>
            <td>tail =  \ l. second [ l (\ h p. pair(list h (first p)) (first p)) (pair empty empty) ]</td>
        </tr>
        <tr>
            <td width="200px">Длина списка</td>
            <td>len = \ l. l (\ h n. succ n) 0</td>
        </tr>
        <tr>
            <td width="200px">Добавление в конец списка</td>
            <td>push_back = \ e l. l list (list e empty) </td>
        </tr>
        <tr>
            <td width="200px">Реверсирование списка</td>
            <td>reverse = \ l. l push_back empty</td>
        </tr>
    </table>
</p>

## ДЗ6
<p>
    <table>
        <tr>
            <td width="200px">Получение последнего элемента списка</td>
            <td>findLast = \ l . l
                (\ h p. if (second p)
                            p
                            (pair h true)
                )
                (pair 0 false)</td>
        </tr>
        <tr>
            <td width="200px">Поиска k-ого элемента списка</td>
            <td>findByIndex = \ l n. if (isEmpty l)
                        (pair 0 false)
                        (if ("=" n 1)
                            (pair (head l) true)
                            (findByIndex (tail l) (pre n))
                        )</td>
        </tr>
        <tr>
            <td width="200px">Проверка, что списки равны</td>
            <td>listEquals = \ l m. if (or (isEmpty l) (isEmpty m))
                       (and (isEmpty l) (isEmpty m))
                       (if ("=" (head l) (head m))
                           (listEquals (tail l) (tail m))
                           false
                       )</td>
        </tr>
        <tr>
            <td width="200px">Проверка, что список является палиндромом</td>
            <td>palindrom = \ l . listEquals l (reverse l)</td>
        </tr>
        <tr>
            <td width="200px">Таблица истинности бинарной функции</td>
            <td>truth_table_2 =
\f. [ list
          (list true (list true (list (f true true) empty)))
          [ list
                (list true (list false (list (f true false) empty)))
                [ list
                      (list false (list true (list (f false true) empty)))
                      [ list
                            (list false (list false (list (f false false) empty)))
                            empty
                      ]
                ]
          ]
    ]</td>
        </tr>
        <tr>
            <td width="200px">Таблица истинности</td>
            <td>truth_table_n = \f n. if (isZero n)
                         # если n = 0, значит мы подставили все аргументы
                         # в исходную функцию, а f -- булевое значение.
                         (list f empty)
                         # иначе получим части таблицы истинности
                         # где первая переменная либо true, либо false
                         # и соединим эти части в одну таблицу
                         (append
                           [truth_table_iteration f n true]
                           [truth_table_iteration f n false]
                         )</td>
        </tr>
        <tr>
            <td width="200px">Вспомогательная функция строит часть таблицы истинности для конкретного значения одной переменной</td>
            <td>truth_table_iteration = \ f n b. add_first_to_elemets
                                            (truth_table_n
                                               (f b) # подставляем аргумент! (\ x y. and x y) b => \ y. and x b
                                               (pre n) # уменьшаем оставшееся количество аргументов
                                            )
                                            b</td>
        </tr>
        <tr>
            <td width="200px">Вспомогательная фунция, принимает список списков l и элемент e</td>
            <td>add_first_to_elemets = \ l e. l
                                # здесь h -- список, к которому нужно приписать элемент e
                                (\ h t. list (list e h) t)
                                empty</td>
        </tr>
        <tr>
            <td width="200px">Бинарное дерево</td>
            <td>btree = \ h l r f x. f h (l f x) (r f x)</td>
        </tr>
        <tr>
            <td width="200px">Рассчёт суммы элементов дерева</td>
            <td>bsum = \ t . t (\ h l r . plus h (plus l r)) 0</td>
        </tr>
        <tr>
            <td width="200px">Максимум</td>
            <td>max = \ a b. if (">=" a b) a b</td>
        </tr>
        <tr>
            <td width="200px">Поиск высоты дерева</td>
            <td>height = \t . t (\h l r. succ (max l r)) 0</td>
        </tr>
        <tr>
            <td width="200px">Пустое поддерево?</td>
            <td>bEmpty = \t . t (\h l r. false) true</td>
        </tr>
        <tr>
            <td width="200px">Проверки симметричности дерева</td>
            <td>bExtract = \ f t . \t. second (t
                      (\ h l r. pair
                                    (btree h (first l) (first r))
                                    (f h l r)
                      )
                      (pair empty empty)
                  )</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>left = bExtract (\ h l r. first l)</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>right = bExtract (\ h l r. first r)</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>bHead = bExtract (\ h l r. h)</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>symmetric = \ t . mirror (left t) (right t)</td>
        </tr>
        <tr>
            <td width="200px"></td>
            <td>mirror = \ a b . if (or (bEmpty a) (bEmpty b))
                    (and (bEmpty a) (bEmpty b))
                    (and (isEqual (bHead a) (bHead b))
                         (and
                           (mirror (left a) (right b))
                           (mirror (right a) (left b))
                         )
                    )</td>
        </tr>
        <tr>
            <td width="200px">Построение вполне сбалансированного дерева, состоящего из n вершин со значением 0</td>
            <td>balancedBTree = \ n .  if (isZero n)
                          empty
                          if ("=" (mod n 2) 1)
                             (btree 0 (balancedBTree (div n 2)) (balancedBTree (div n 2)))
                             (btree 0 (balancedBTree (div n 2)) (balancedBTree (pre (div n 2))))</td>
        </tr>
    </table>
</p>
