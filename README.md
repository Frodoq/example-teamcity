 В YC создал новые инстансы (4CPU4RAM) на основе образа jetbrains/teamcity-server и jetbrains/teamcity-agent, дождался запуска teamcity, выполнил первоначальную настройку, авторизовал агент:
 <img width="1504" height="269" alt="image" src="https://github.com/user-attachments/assets/b33ee611-774c-4c4d-a73b-37c5b36fe839" />
 <img width="793" height="364" alt="image" src="https://github.com/user-attachments/assets/0b1afe2b-ca0e-4b96-87fd-f3ea72b77334" />


Сделал fork репозитория и клонировал на ВМ

Создал VM (2CPU4RAM) и запустил плейбук https://github.com/netology-code/mnt-homeworks/blob/MNT-video/09-ci-05-teamcity/infrastructure

решение задания:

1. Создал новый проект в teamcity на основе fork.
<img width="1501" height="544" alt="image" src="https://github.com/user-attachments/assets/1835f29b-a87f-4c17-a868-23fee511a564" />
2. Сделайте autodetect конфигурации.
<img width="1513" height="571" alt="image" src="https://github.com/user-attachments/assets/19b44f20-a67d-4cda-976e-f048e64f485d" />
3. Сохраните необходимые шаги, запустите первую сборку master.
<img width="1360" height="450" alt="image" src="https://github.com/user-attachments/assets/3d042bcf-99a0-49f8-a66b-a5bdebc1b1f6" />
4. Поменяйте условия сборки: если сборка по ветке master, то должен происходит mvn clean deploy, иначе mvn clean test.
<img width="1533" height="644" alt="image" src="https://github.com/user-attachments/assets/0b3767a5-5187-4e21-86d5-7465a074594e" />
5. Для deploy загрузил settings.xml в набор конфигураций maven у teamcity, предварительно записав туда креды для подключения к nexus.
6. В pom.xml поменял ссылки на репозиторий и nexus.
   https://github.com/Frodoq/example-teamcity/blob/master/pom.xml
7. Запустите сборку по master, убедитесь, что всё прошло успешно и артефакт появился в nexus.
<img width="1089" height="456" alt="image" src="https://github.com/user-attachments/assets/a62e43e2-4300-43e1-a460-9ca9878261dd" />
8. Мигрировал build configuration в репозиторий.
9. Создал отдельную ветку feature/add_reply в репозитории.
10. Напишите новый метод для класса Welcomer: метод должен возвращать произвольную реплику, содержащую слово hunter.

'''
package plaindoll;

public class Welcomer{
	public String sayWelcome() {
		return "Welcome home, good hunter. What is it your desire?";
	}
	public String sayFarewell() {
		return "Farewell, good hunter. May you find your worth in waking world.";
	}
	public String sayNeedGold(){
		return "Not enough gold";
	}
	public String saySome(){
		return "something in the way";
	}
	public String sayHunter() {
		return "Please take care of yoursalf, hunter.";
  }
}
'''
11. 
Дополните тест для нового метода на поиск слова hunter в новой реплике.
Сделайте push всех изменений в новую ветку репозитория.
Убедитесь, что сборка самостоятельно запустилась, тесты прошли успешно.
Внесите изменения из произвольной ветки feature/add_reply в master через Merge.
Убедитесь, что нет собранного артефакта в сборке по ветке master.
Настройте конфигурацию так, чтобы она собирала .jar в артефакты сборки.
Проведите повторную сборку мастера, убедитесь, что сбора прошла успешно и артефакты собраны.
Проверьте, что конфигурация в репозитории содержит все настройки конфигурации из teamcity.
В ответе пришлите ссылку на репозиторий.
