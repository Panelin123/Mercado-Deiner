#include <stdio.h>
#include <string.h>

#define MAX_PRODUTOS 10
#define MAX_CARRINHO 10

typedef struct {
    int codigo;
    char nome[30];
    float preco;
} Produto;

typedef struct {
    Produto produto;
    int quantidade;
} ItemCarrinho;

Produto estoque[MAX_PRODUTOS];
ItemCarrinho carrinho[MAX_CARRINHO];
int total_produtos = 0;
int total_itens_carrinho = 0;

void cadastrarProduto() {
    if (total_produtos < MAX_PRODUTOS) {
        Produto p;
        printf("Digite o codigo do produto: ");
        if (scanf("%d", &p.codigo) != 1) {
            printf("Erro na leitura do codigo!\n");
            return;
        }
        printf("Digite o nome do produto: ");
        getchar(); // Limpa o buffer
        fgets(p.nome, sizeof(p.nome), stdin);
        p.nome[strcspn(p.nome, "\n")] = 0; // Remove o newline
        printf("Digite o preco do produto: ");
        if (scanf("%f", &p.preco) != 1) {
            printf("Erro na leitura do preco!\n");
            return;
        }
        estoque[total_produtos++] = p;
        printf("Produto cadastrado com sucesso!\n");
    } else {
        printf("Estoque cheio!\n");
    }
}

void listarProdutos() {
    printf("Produtos cadastrados:\n");
    for (int i = 0; i < total_produtos; i++) {
        printf("Codigo: %d, Nome: %s, Preco: %.2f\n", estoque[i].codigo, estoque[i].nome, estoque[i].preco);
    }
}

void comprarProduto() {
    int codigo, quantidade;
    printf("Digite o codigo do produto que deseja comprar: ");
    scanf("%d", &codigo);
    printf("Digite a quantidade: ");
    scanf("%d", &quantidade);
    
    for (int i = 0; i < total_produtos; i++) {
        if (estoque[i].codigo == codigo) {
            if (total_itens_carrinho < MAX_CARRINHO) {
                carrinho[total_itens_carrinho].produto = estoque[i];
                carrinho[total_itens_carrinho].quantidade = quantidade;
                total_itens_carrinho++;
                printf("Produto adicionado ao carrinho!\n");
            } else {
                printf("Carrinho cheio!\n");
            }
            return;
        }
    }
    printf("Produto nao encontrado!\n");
}

void visualizarCarrinho() {
    printf("Produtos no carrinho:\n");
    for (int i = 0; i < total_itens_carrinho; i++) {
        printf("Codigo: %d, Nome: %s, Quantidade: %d, Preco: %.2f\n",
               carrinho[i].produto.codigo, carrinho[i].produto.nome,
               carrinho[i].quantidade, carrinho[i].produto.preco);
    }
}

int main() {
    int opcao;
    do {
        printf("1. Cadastrar Produto\n");
        printf("2. Listar Produtos\n");
        printf("3. Comprar Produto\n");
        printf("4. Visualizar Carrinho\n");
        printf("5. Sair\n");
        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);
        
        switch (opcao) {
            case 1:
                cadastrarProduto();
                break;
            case 2:
                listarProdutos();
                break;
            case 3:
                comprarProduto();
                break;
            case 4:
                visualizarCarrinho();
                break;
            case 5:
                printf("Saindo...\n");
                break;
            default:
                printf("Opcao invalida!\n");
        }
    } while (opcao != 5);

    return 0;
}
