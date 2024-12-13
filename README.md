import java.util.Scanner;

public class Shopping {
    public static void main(String[] args) {

        System.out.println("Вас приветствует список покупок!");

        String[] shoppingList = new String[8];
        int productCount = 0;

        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("Выберите одну из команд:");
            System.out.println("1. Добавить товар в список");
            System.out.println("2. Отобразить список");
            System.out.println("3. Очистить список");
            System.out.println("4. Завершить программу");
            System.out.print("Ваш выбор: ");

            int actionNumber;
            if (!(scanner.hasNextInt())) { // Здесь я проверяю, что бы пользователь ввел целое число, а не что-то иное
                System.out.println("Введите корректный номер");
                scanner.next(); // Здесь очищаю ввод пользователя.
            } else {
                actionNumber = scanner.nextInt();
                scanner.nextLine(); // Очищаем буфер

                // Начинаем проверять ввод пользователя
                if (actionNumber == 1) {
                    if (productCount < shoppingList.length) {
                        System.out.print("Введите название товара: ");
                        String product = scanner.nextLine();

                        boolean searchForDuplicates = false;

                        for (int i = 0; i < productCount; i++) {
                            if (shoppingList[i].equalsIgnoreCase(product)) {
                                searchForDuplicates = true;
                                break;
                            }
                        }

                        if (!(searchForDuplicates)) {
                            shoppingList[productCount] = product;
                            System.out.println("Товар " + product + " добавлен в список под номером " + (productCount + 1));
                            productCount++;
                        } else {
                            System.out.println("Такой товар уже есть. Укажите другой!");
                        }


                    } else {
                        System.out.println("Извините, список полон!");
                    }
                } else if (actionNumber == 2) {
                    if ((productCount != 0)) {
                        System.out.println("Список покупок:");
                        for (int i = 0; i < productCount; i++) {
                            System.out.println((i + 1) + "." + shoppingList[i]);
                        }
                    } else {
                        System.out.println("Список товаров пуст!");
                    }
                } else if (actionNumber == 3) {
                    productCount = 0;
                    System.out.println("Список очищен!");
                } else if (actionNumber == 4) {
                    System.out.println("До скорых встреч!");
                    return;
                } else {
                    System.out.println("Неизвестная команда!");
                }
            }
        }
    }
}
