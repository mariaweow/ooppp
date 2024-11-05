from pprint import pprint
cook_book = {}
with open('recipes.txt', 'rt', encoding='utf-8') as file:
    dishes = ''
    for x in file:
        x = x.strip()
        if x.isdigit():
            continue
        elif x and '|' not in x:
            cook_book[x] = []
            dishes = x
        elif x and '|' in x:
            a, b, c = x.split(" | ")
            cook_book.get(dishes).append(dict(ingredient_name=a, quantity=int(b), measure=c))

pprint(cook_book)


#задача 2
def get_shop_list_by_dishes(dishes_list, person_count):
    shop_list = {}
    for dish in dishes_list:
        if dish in cook_book:
            for ingredient in cook_book[dish]:
                if ingredient['ingredient_name'] in shop_list:
                    shop_list[ingredient['ingredient_name']]['quantity'] += ingredient['quantity'] * person_count
                else:
                    shop_list[ingredient['ingredient_name']] = ({'measure': ingredient['measure'], 'quantity':
                                                                (ingredient['quantity'] * person_count)})
        else:
            print('Такого блюда нет в книге')
    return shop_list


pprint(get_shop_list_by_dishes(['Фахитос', 'Омлет'], 2))
  

#задача 3
def readfile(path: str):
    files_list = os.listdir(path) 
    text = {} 
    for some_file in files_list:
        if some_file.rfind('.txt', -4): 
          with open(os.path.join(path, some_file), 'r', encoding='utf-8') as file:
            text[some_file] = file.readlines()
 
    with open('final_file.txt', 'w', encoding='utf-8') as file:
      
        for file_name, rows in sorted(text.items, key=lambda x: x[1]):  
            file.write(final_file.txt + '\n')
            file.write(str(len(rows)) + '\n')
            if '\n' not in rows[-1]:
                rows[-1] += '\n'
            file.write(''.join(rows))
 
 
readfile(path)
