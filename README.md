import matplotlib.pyplot as plt
from matplotlib_venn import venn3

v = set(['Альдегиды', 'Кожаный аккорд', 'Шафран', 'Боярышник', 'Мускус', 'Сирень', 'Стиракс', 'Клейкая лента (скотч)', 'Промышленный клей', 'Ананас', 'Грейпфрут', 'Клубника', 'Маракуйя', 'Танжерин', 'Красный кедр', 'Ваниль','Бергамот', 'Кактус', 'Клементин'])
s = set(['Альдегиды', 'Кожаный аккорд', 'Шафран', 'Боярышник', 'Мускус', 'Сирень', 'Стиракс', 'Клейкая лента (скотч)', 'Промышленный клей', 'Ландыш', 'Пион', 'Розовый перец', 'Жасмин', 'Фиалка', 'Иланг-иланг', 'Ревень', 'Роза', 'Сирень', 'Жасмин'])
b = set(['Альдегиды', 'Кожаный аккорд', 'Шафран', 'Боярышник', 'Мускус', 'Сирень', 'Стиракс', 'Клейкая лента (скотч)', 'Промышленный клей', 'Древесный аккорд', 'Дубовый мох', 'Амбра', 'Белый кедр', 'Сандал', 'Стиракс', 'Персик', 'Сирень', 'Лимонное дерево', 'Нектарин'])
plt.figure(figsize=(16,16))
diagram = venn3([v, s, b], ('Верхние ноты души', 'Средние ноты сердца', 'Базовые ноты'))

diagram.get_label_by_id("111").set_text("\n".join(v & s))
diagram.get_label_by_id("100").set_text("\n".join(v - s - b))
diagram.get_label_by_id("010").set_text("\n".join(s - v - b ))
diagram.get_label_by_id("001").set_text("\n".join(b - s - v))
diagram.get_label_by_id("110").set_text("\n".join(v & s - b))
diagram.get_label_by_id("011").set_text("\n".join(b & s - v))
diagram.get_label_by_id("101").set_text("\n".join(v & b - s))

for text in diagram.set_labels:
text.set_fontsize(25)
for text in diagram.subset_labels:
text.set_fontsize(15)
plt.figure(figsize=(100,100))
plt.show()
