# QuerySet

Получить 5 последних написанных комментариев (именно текст)

> CommentToArticle.objects.all()[:5].values('comment')

![1](https://user-images.githubusercontent.com/33054469/110189382-91ceb700-7e27-11eb-99ee-a976d2b2a430.png)

<hr>

Создать 5 комментариев с разным текстом, Хотя бы один должен начинаться со слова "Start", хоть один в середине должен иметь слово "Middle", хоть один должен заканчиваться словом "Finish".

>  CommentToArticle.objects.create(author = a, article = ar,  comment='Seredina eto middle') <br>
>  CommentToArticle.objects.create(author = a, article = ar,  comment='Start tut stoit pervim') <br>
>  CommentToArticle.objects.create(author = a, article = ar,  comment='A tut stoit poslednim FinIsH')<br>

![2](https://user-images.githubusercontent.com/33054469/110189833-40bfc280-7e29-11eb-896d-f29fa640f188.png)

<hr>

Переписать сейв комментария так, что бы при создании дата менялась бы на год назад (если сегодня 20 декабря 2019, должна выставляться 20 декабря 2018), изменение комментариев не затрагивать.

> CommentToArticle.objects.filter(id=15).update(created_at=datetime.now() - timedelta(days=365))

(я видел про григорианский календарь но как сделать привязку с високосным ХЗ)
![time1](https://user-images.githubusercontent.com/33054469/110190019-f854d480-7e29-11eb-903a-a7fafb0dae78.png)
![поменяна дата](https://user-images.githubusercontent.com/33054469/110190066-32be7180-7e2a-11eb-8374-337573855349.png)

<hr>

Изменить комментарии со спец словами "Start", "Middle", "Finish".

![изсенения по части текста](https://user-images.githubusercontent.com/33054469/110190169-9fd20700-7e2a-11eb-988c-b45010ed0919.png)

<hr>

Удалить все комментарии у которых в тексте есть буква "k", но не удалять если есть буква "с".

> CommentToArticle.objects.filter(comment__contains='k').exclude(comment__contains='c').delete() <br>

![delete222](https://user-images.githubusercontent.com/33054469/110190369-9d23e180-7e2b-11eb-9207-ae3b017ede8e.png)

<hr>

Получить первые 2 коментария по дате создания к статье у которой имя автора последнее по алфавиту.

> authorInTheEnd = Author.objects.order_by('name')[0] <br>
> CommentToArticle.objects.filter(author = authorInTheEnd).order_by('created_at')[2:] <br>

![konec](https://user-images.githubusercontent.com/33054469/110190472-1faca100-7e2c-11eb-96d7-50c6b003d72f.png)

<hr>

До  7 не добрался


