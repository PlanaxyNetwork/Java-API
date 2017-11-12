# Java API

- PCA (Persistence Command API)
  Feita por David, na versão 1.2
# Descrição - PCA
*Utilitarios para programadores Java, para criar comandos com argumentos.
# Como Utilizar - PCA


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
	
- SDU (SimpleDate Utils)
  Feita por David, na versão 1.2
# Descrição - SDU
*Utilitarios para programadores Java, para facilitar a vida de quem trabalha com Date.
# Como Utilizar - SDU


		public static void main(String[] args) {

		System.out.println("-=-=-=-=-=-=-=-SimpleDate=-=-=-=-=-=-=-=-=-=-");

		System.out.println("SimpleDate Exemplos: \n");

		System.out.println("Pegar data do Sistema: ");
		SimpleDate data = new SimpleDate();// data do sistema

		System.out.println("String normal: " + data.toDateString() + "\n");

		System.out.println("Fazer Formato por Metodos:");
		System.out.println("Metodos: " + data.getDay() + "/" + data.getMonth() + "/" + data.getYear() + "\n");

		System.out.println("-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-");

		System.out.println("Fazer uma data: ");
		data = new SimpleDate(20, 02, 2012);

		System.out.println("String normal: " + data.toDateString() + "\n");

		System.out.println("Fazer Formato por Metodos:");
		System.out.println("Metodos: " + data.getDay() + "/" + data.getMonth() + "/" + data.getYear() + "\n");

		System.out.println("-=-=-=-=-=-=-=-=-SimpleFormatter=-=-=-=-=-=-=-=-=-\n");
		System.out.println("SimpleFormatter Exemplos:");

		data = new SimpleDate(); // data do sistema

		SimpleFormatter formatter = new SimpleFormatter(data);

		String meuFormato = (((IFormatable)formatter).format("DD/MM/YYYY - HH:MIN:SS"));

		System.out.println("Meu Formato: " + meuFormato);

		meuFormato = (((IFormatable)formatter).format("[DD|MM|YYYY]:[HH|MIN|SS]"));

		System.out.println("Outro Formato: " + meuFormato + "\n");

		System.out.println("-=-=-=-=-=-=-=-=-Expirable e Comparable=-=-=-=-=-=-=-=-=-\n");
		System.out.println("Exemplos (Expirable):\n");

		SimpleDate proximoAniversario = new SimpleDate(22,07,2017);

		SimpleDate dataAtual = new SimpleDate();

		System.out.println("Testar Em: " + proximoAniversario.toDateString() + " / " + dataAtual.toDateString());

		boolean expirou = ((IExpirable<SimpleDate>)dataAtual).isExpired(proximoAniversario);
		if(expirou){

			System.out.println("R: Seu Aniversario passou!");
		}else{

			System.out.println("R: Seu aniversario ainda nao Chegou.");
		}

		System.out.println("Exemplos (Comparable):\n");

		SimpleDate primeiraData = new SimpleDate(20, 02, 2017);
		SimpleDate segundaData = new SimpleDate(20, 02, 2017);

		System.out.println("Teste 1: [" + primeiraData.toDateString() + " - " + segundaData.toDateString() + "]");
		boolean comparavel = ((IComparable<SimpleDate>)(primeiraData)).compare(segundaData);
		if(comparavel){
			System.out.println("A Primeira Data e Igual a Segunda.\n");
		}
		else{
			System.out.println("A Primeira Data nao e Igual a Segunda.\n");
		}

		segundaData = new SimpleDate(22, 04, 2018);

		System.out.println("Teste 1: [" + primeiraData.toDateString() + " - " + segundaData.toDateString() + "]");
		comparavel = ((IComparable<SimpleDate>)(primeiraData)).compare(segundaData);
		if(comparavel){
			System.out.println("A Primeira Data e Igual a Segunda.\n");
		}
		else{
			System.out.println("A Primeira Data nao e Igual a Segunda.\n");
		}

	}
