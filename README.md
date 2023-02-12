# <center>Project 2. Анализ резюме на HeadHunter</center> 

<center><img src = https://raw.githubusercontent.com/AndreyRysistov/DatasetsForPandas/main/hh%20label.jpg alt="drawing" style="width:400px;"></center> 

<font size=4> 

## Содержание

[1. Введение](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#1-%D0%B2%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5)   
[2. Описание задачи](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#2-%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B8)   
[3. Описание данных](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#3-%D0%BE%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85)         
[4. Результат](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#4-%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82)          
[5. Выводы](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#5-%D0%B2%D1%8B%D0%B2%D0%BE%D0%B4%D1%8B)       


## 1. Введение

Кадровое агентство, подбирающее вакансии для IT-специалистов, создаёт модель машинного обучения, которая будет рекомендовать вакансии клиентам агентства,претендующим на позицию Data Scientist. До построения модели необходимо понять, что из себя представляют данные и насколько они соответствуют целям проекта. В литературе эта часть работы над ML-проектом называется Data Understanding, или анализ данных. 

 :arrow_up:[к содержанию](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5)      


## 2. Описание задачи

Наш проект включает в себя несколько этапов:    
   * знакомство с данными;
   * предварительный анализ данных;
   * детальный анализ вакансий;
   * анализ работодателей;
   * предметный анализ.
   
Каждый этап состоит из блока практических заданий, которые необходимо выполнить в jupyter-ноутбуке.     

Требования к оформлению ноутбука-решения:

 * Решение оформляется только в Jupyter Notebook.
 * Решение оформляется в соответствии с ноутбуком-шаблоном.
 * Каждое задание выполняется в отдельной ячейке, выделенной под задание (в шаблоне они помечены как ваш код здесь). Не следует создавать много ячеек для решения задачи — это провоцирует неудобства при проверке.
 * Текст SQL-запросов и код на Python должны быть читаемыми. Не забывайте про отступы в SQL-коде.
 * Выводы по каждому этапу оформляются в формате Markdown в отдельной ячейке (в шаблоне они помечены как ваши выводы здесь).
 * Выводы можно дополнительно проиллюстрировать с помощью графиков. Они оформляются в соответствии с теми правилами, которые мы приводили в модуле по визуализации данных.
 * Не забудьте удалить ячейку с данными соединения перед фиксацией работы в GitHub.
       
 :arrow_up:[к содержанию](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5)    


## 3. Описание данных

Все необходимые таблицы находятся в схеме public базы данных project_sql.
Посмотрим на общую структуру базы данных:


<center><img src = https://lms.skillfactory.ru/assets/courseware/v1/efd63819603e7d4f4433ed2fedec717c/asset-v1:SkillFactory+DSPR-2.0+14JULY2021+type@asset+block/SQL_pj2_2_1.png style="width:500px;height:500px"></center> 

Познакомимся с каждой таблицей.

**VACANCIES**           
Таблица хранит в себе данные по вакансиям и содержит следующие столбцы:

<center><img src = https://lms.skillfactory.ru/assets/courseware/v1/837cf6ff79f483e387a16c993634f3e4/asset-v1:SkillFactory+DSPR-2.0+14JULY2021+type@asset+block/SQL_pj2_2_2.png style="width:800px;height:400px"></center> 

Зарплатная вилка — это верхняя и нижняя граница оплаты труда в рублях (зарплаты в других валютах уже переведены в рубли). Соискателям она показывает, в каком диапазоне компания готова платить сотруднику на этой должности.

**AREAS**            
Таблица-справочник, которая хранит код города и его название:

<center><img src = https://lms.skillfactory.ru/assets/courseware/v1/682c2306f3d46a25915a89d4ec7e16ed/asset-v1:SkillFactory+DSPR-2.0+14JULY2021+type@asset+block/SQL_pj2_2_3.png style="width:800px;height:120px"></center> 

**EMPLOYERS**          
Таблица-справочник со списком работодателей:

<center><img src = https://lms.skillfactory.ru/assets/courseware/v1/d2a26db623c75572c71923b57241e038/asset-v1:SkillFactory+DSPR-2.0+14JULY2021+type@asset+block/SQL_pj2_2_4.png style="width:800px;height:150px"></center> 

**INDUSTRIES**         
Таблица-справочник вариантов сфер деятельности работодателей:

<center><img src = https://lms.skillfactory.ru/assets/courseware/v1/2c76bca09937a1a05a9e66d51008e298/asset-v1:SkillFactory+DSPR-2.0+14JULY2021+type@asset+block/SQL_pj2_2_5.png style="width:800px;height:120px"></center> 

**EMPLOYERS_INDUSTRIES**            
Дополнительная таблица, которая существует для организации связи между работодателями и сферами их деятельности:

<center><img src = https://lms.skillfactory.ru/assets/courseware/v1/16ff3df0bb0ddecd922562f3c4bdd32c/asset-v1:SkillFactory+DSPR-2.0+14JULY2021+type@asset+block/SQL_pj2_2_6.png style="width:800px;height:120px"></center> 

Эта таблица нужна нам, поскольку у одного работодателя может быть несколько сфер деятельности (или работодатели могут вовсе не указать их). Для удобства анализа необходимо хранить запись по каждой сфере каждого работодателя в отдельной строке таблицы.
        
 :arrow_up:[к содержанию](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5)      


## 4. Результат

Для отображения интерактивных графиков ссылка на ноутбук через сервис nbviewer: [Project_2.ipynb](https://nbviewer.org/github/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter/blob/5baa8e7f07e70ff5c3977a9678a6f45969b43a43/Project_2.ipynb)             
Ссылка на ноутбук с решением на github: [Project_2.ipynb](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter/blob/master/Project_2.ipynb).                
Для обеспечения воспроизводимости кода можно воспользоваться: [requirements.txt](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter/blob/master/requirements.txt).                        

 :arrow_up:[к содержанию](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5)        


## 5. Выводы

В данном проекте была проведена работа по анализу данных содержащих предложения по вакансиям. Данные выгружалися из учебной базы данных project_sql. Для подключения данных использовалась библиотека sqlalchemy. Проведены дополнительные исследования данных с использованием визуализации (бибилиотека plotly).
      
Почта для обратной связи: vasilevdma82@gmail.com                 

 :arrow_up:[к содержанию](https://github.com/DmitVasilev/Project_2-Analysis-resume-on-HeadHunter#%D1%81%D0%BE%D0%B4%D0%B5%D1%80%D0%B6%D0%B0%D0%BD%D0%B8%D0%B5)  