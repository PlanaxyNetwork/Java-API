# Java API

- PCA (Persistence Command API)
  Feita por David, na versão 1.2
# Descrição - PCA
*Utilitarios para programadores Java, para criar comandos com argumentos.
# Como Utilizar - PCA

`
import java.util.List;

public class Main {

	public static void main(String[] args) {
		
		Printable printable = new PrintableAdapter() {
			public void append(String o) {
				System.out.println(o);
			}
		};
		
		CommandLoader commandLoader = new CommandLoader(printable);
		
		commandLoader.getCommands().put("teste", new CommandExecutor() {
			public boolean onCommand(String command, List<String> arguments, int size, Printable print, String label) {
				if(command.equals(getCommand())){
					System.out.println("ARG 0: " + arguments.get(0));
				}
				
				return false;
			}
		});
		
		commandLoader.updateRegisters();
		
		commandLoader.compile("/teste 123");
		
	}
	
}


`
