**Отчёт о тестировании Credit Card Number Validator**

**Краткое описание тесстирования**

07/01/2021 - 07/01/2021 было проведено функциональное тестирование приложения Credit Card Number Validator.
На тестирование затрачено 3.5 часа.

В результате тестирования выявлен следующий дефект:
- https://github.com/larlarlar/Credit-Card-Number-Validator/issues/2#issue-781603065

**Описание процесса тестирования**

Объект тестирования - код, представленный программистом:

public class Main {

  public static void main(String[] args) {
  
    // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов
    
    String number = "5351719427810741";
    
    System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
    
  }
  
  public static boolean isValidCardNumber(String number) {
  
    if (number == null) {
    
      return false;
      
    }
    
    if (number.length() != 16) {
    
      return false;
      
    }
    
    long result = 0;
    
    for (int i = 0; i < number.length(); i++) {
    
      int digit;
      
      try {
      
        digit = Integer.parseInt(number.charAt(i) + "");
        
      } catch (NumberFormatException e) {
      
        return false;
        
      }
      
      if (i % 2 == 0) {
      
        digit *= 2;
        
        if (digit > 9) {
        
          digit -= 9;
          
        }
        
      }
      
      result += digit;
      
    }
    
    return (result != 0) && (result % 10 == 0);
    
  }
  
}

В качестве тестовых данных использовались сгенерированные номера карт. Источник: https://www.kobzarev.com/other/testoviye-nomera-kreditnyh-kart/#tablica-testovyh-kart

Окружение:

- ОС: Windows 10 домашняя, 64-разрядная операционная система, процессор х64
- openjdk version "11.0.9.1" 2020-11-04
  OpenJDK Runtime Environment AdoptOpenJDK (build 11.0.9.1+1)
  OpenJDK 64-Bit Server VM AdoptOpenJDK (build 11.0.9.1+1, mixed mode)
- Toolbox App Version: 1.19, Released: 18 December 2020
- IntelliJ IDEA Community Edition 2020.3.1
