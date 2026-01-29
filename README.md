# proj.bibli

Using System;
Using System.Bibli;

namespace PROJE.BIBLI

public class Main {
    static List<Livro> acervo = new ArrayList<>();
    static List<Cliente> clientes = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {
        // Dados Iniciais
        acervo.add(new Livro("101", "Peter Pan", "J. M. Barrie"));
        clientes.add(new Cliente("111", "João Silva"));

        int op = -1;
        while (op != 0) {
            System.out.println("\n--- BIBLIOTECA LIVROS ---");
            System.out.println("1. Listar Livros | 2. Cadastrar Livro | 3. Empréstimo | 4. Devolução | 0. Sair");
            System.out.print("Opção: ");
            op = Integer.parseInt(sc.nextLine());

            switch (op) {
                case 1: acervo.forEach(System.out::println); break;
                case 2: cadastrarLivro(); break;
                case 3: realizarEmprestimo(); break;
                case 4: realizarDevolucao(); break;
            }
        }
    }

    static void cadastrarLivro() {
        System.out.print("ISBN: "); String isbn = sc.nextLine();
        System.out.print("Título: "); String tit = sc.nextLine();
        System.out.print("Autor: "); String aut = sc.nextLine();
        acervo.add(new Livro(isbn, tit, aut));
        System.out.println("Sucesso!");
    }

    static void realizarEmprestimo() {
        System.out.print("ISBN do Livro: "); String isbn = sc.nextLine();
        for (Livro l : acervo) {
            if (l.isbn.equals(isbn) && l.disponivel) {
                l.disponivel = false;
                System.out.println("Empréstimo realizado!");
                return;
            }
        }
        System.out.println("Livro não disponível.");
    }

    static void realizarDevolucao() {
        System.out.print("ISBN do Livro: "); String isbn = sc.nextLine();
        for (Livro l : acervo) {
            if (l.isbn.equals(isbn) && !l.disponivel) {
                l.disponivel = true;
                System.out.println("Devolução realizada!");
                return;
            }
        }
        System.out.println("Erro na devolução.");
    }
}

https://app.diagrams.net/#G1t57FAHiM7wpO-VSbdeFK2JPLLPMxhfAJ#%7B%22pageId%22%3A%22iMJr1AqXTBClZb3xq0cb%22%7D
