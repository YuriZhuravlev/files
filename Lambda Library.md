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
            <td width="200px">Пустотой список</td>
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
