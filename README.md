// Trabalho-M1-algoritmos-2
//alunos: Victor André Uller e Eduardo Souza Cruz Accácio
#include <iostream>
#include <locale.h>
#include <stdlib.h>
#include <time.h>
#include <fstream>
using namespace std;
/* Sumário
47 - torneio
97 templo
210 casa
234 início
301 restaurante
335 homem dos jogos
378 loja
450 floricultura
493 menu
549 main*/
//Uma struct para o protagonista que armazenará todos os seus status.
struct personagem{
string nome, sapato="pés descalços";
int bolso=30, carisma=4;

//agora as variáveis são referentes aos personágens secundários, quando se tornam 0, quer dizer que ele desgosta do protagonista
bool vizinha=1, julia=0, monge=1, atendente=1, homem=0;

/*Variáveis referentes a locais onde o protagonista ja passou, ou acões já feitas, lugares são iguais a 1 e se tornam 0 apos
serem feitas para que não passem pelo filtro if, e as ações o oposto.*/
bool inscricao=0, restaurante=1, templo=1, torneio=1, tapa=0, cenafinal=1;
};

//class para a loja
class prod{
public: string nome;
public: int preco;
};

//função para escolhas entre duas ações
void escolha2(string &act){
    act = "a";
while(act != "0" and act != "1"){
  cin >> act;
}
return;
}

///Tela de início---------------------------------------------------------------------------------------------------------------
void tela_de_inicio(){
    string t;
cout << "\t Tela de início\n\
\nPor: Victor André Uller e Eduardo Souza Cruz Accácio\n\ninsira qualquer tecla para jogar ";
cin >> t;
}

///Torneio, Parte final---------------------------------------------------------------------------------------------------------
void torneio(personagem &prota){
system("cls");
cout << "É chegado o dia, você vai até o templos para duelar e vencer o torneio\n\
O torneio começa e você já caiu no primeiro duelo do dia. Você vai até a arena e tem cerca de 50 pessoas na plateia\n\
Porém, antes que fosse iniciado o duelo um homem aparece correndo com papeis nas mãos e gritando \"Pessoal, Pessoal, o torneio acaba de\
ser cancelado devido a problemas internos.\"\n\n\
Monje:\"Ó não. Tudo bem,portanto, teremos que decidir quem é o vencedor do torneio por nós mesmos. Vamos as opinões.\n\n\"";
if(prota.monge){
    cout << "Monge:\"Eu voto que o " << prota.nome << " deve vencer, ele é um rapaz ótimo e muito dedicado nos duelos\"";
} else {
    prota.carisma = prota.carisma - 1;
    cout << "Monge:\"Primeiro, eu nãogosto do " << prota.nome << ", ele é uma pessoa terrivel e extemamente inconveniente. Não deve ganhar!\n\n";
}

if(prota.vizinha){
    cout << "\n\nVizinha:\"Até que ele é um moço legal, por mim ele deve ganhar\"";
} else {
    prota.carisma = prota.carisma - 1;
    cout << "\n\nVizinha:\"Ele é um maluco, não merece ganhar de geito nenhum\"";
}
if(prota.julia){
    cout << "\n\nJúlia:\"Ele é INCRIVELLL, uma pessoa exelente e muito boa em duelos\"";
} else {
    prota.carisma = prota.carisma - 1;
    cout << "\n\nJúlia:\"Não, ELE È UMA PESSOA HORRÍVEL.>w<\"";
}
if(prota.atendente){
    cout << "\n\nAtendente:\"Ele é um rapaz muito interessante, por mim a vitória é dele\"";
} else {
    prota.carisma = prota.carisma - 1;
    cout << "\n\nAtendente:\"ELE SAIU DO MEU RESTAURANTE SEM PAGAR, que carater deplorável, não ganhará!\"";
}
if(prota.homem){
    cout << "\n\nCara do Par ou Impar:\"Ele é muito legaalll ToT deixem-o ganhar\"";
}
if(prota.carisma >= 2){
    cout << "\n\nPlateia:\ÉÉÉÉÉÉÉÉÉÉÉÉÉ, esse cara dos " << prota.sapato << " é mesmo muito bom viva elee viva\"";
    cout << "\n\nEmbora sem lutas, você conseguiu ganhar o torneio, as lutas terão que ficar para putro dia, mas as pessoas gostam muito de você";
} else {
    cout << "Plateia:\" UUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUU! esse cara dos " << prota.sapato << " é muito ruim\"\n\
    Espectador:\"Sai daí seu mané\"\n\n\
    Você perdeu o grande torneio e voltou cabisbaixo para casa, não pela derrota, mas pois queria ter lutado hoje..\n\n";
}
cout << "\n\nE é assim que acaba essa boa jornada, foi uma honra ter as suas atitudes nessa estória\n\
Insira qualquer tecla: ";
cin >> prota.sapato;
prota.torneio = 0;
}

///Templo-----------------------------------------------------------------------------------------------------------------------
void templo(personagem &prota, bool horario, string act){
system("cls");
if(horario){
cout << "\n\n\nVocê vai até lá e as luzes estão apagadas, como ja frequentou muito o recinto, você vai direto à porta de quem procura.\n\
Você bate na porta, mas ninguém o atende:\n\n\
0 > Voltar para casa\n\n\
1 > Bater com mais força\n\n\
2 > Abrir com a chave debaixo do tapete e entrar\n\
act: \n\n";
act = "a";
while(act != "0" and act != "1" and act != "2"){
 cin >> act;
}
 if(act == "0"){
    return;
 } else if(act == "1"){
 cout << "\nUm outro monge te atende e diz:\n\n\
 Monge:\"O que aconteceu?\"\n\n\
 Você:\"Aconteceu que o seu melhor competidor veio se inscrever no campionato :).\"\n\n";
 }else{
 cout << "Você entra no cômodo e acorda o monge com tapas na careca.\n\n\
 Monge\"Que inconveniência é essa? Por que você está aqui?\"\n\n\
 Você:\"Vim para me inscrever no torneio!! :D\"\n\n";
 prota.monge = 0;
 prota.tapa = 1;
 }
 cout << "Monge:\"Você deveria aprender bons modos, saia daqui e volte amanhã\"\n\n\
 0 > \"Não tente aborrecer um homem de classe como eu, não me faça vir atoa ou medids serão tomadas.\"\n\n\
 1 > \"Tudo bem, acabo de aprender bons modos e retornarei amanhã\"\n\
 act: \n\n";
 escolha2(act);
if(act == "1"){
        if(prota.tapa){
    prota.bolso = prota.bolso + 30;
    cout << "\nconquista: tapa na careca. +R$30\n precione uma tecla:";
}
    return;
} else{
cout << "\nVários monges do quarto se levantam e começam a te espancar\"\n\n\
Você: Parem, a Júia me pediu para entregar esse bilhete\"\n\n\
*Você entrega a ficha a eles*\n\n\
Monje:\"Tudo bem, mas se vieres até mim novamente com tamanha ousadia denovo, a surra será sem pausa\"\n\n\
Agora você ja está inscrito no torneio e volta para casa para dormir.\nInsira uma tecla: ";
if(prota.tapa){
    prota.bolso = prota.bolso + 30;
    cout << "\nconquista: tapa na careca. +R$30";
}
cin >> act;
prota.inscricao = 1;
}
} else {
    prota.templo = 0;
cout << "Você vai até o templo para treinar\n";

//ela foi setada inicialmente como 0 para que essa cena pudece ser variada com mais facilidade
if(prota.julia){
    cout << "A júlia aparece para falar com você\n\n\
    Júlia:\"Olá amigo, lembra de mim? já fez sua inscrição para o teorneio c:?\"";
    if(prota.inscricao){
        cout << "\n\nVocê:\"Certamente, fui ainda ontem";


    } else {
      cout << "Você:\"Saldação, ainda não, estava indo fazê-la agora mesmo\"\n\n\
      Júlia:\"Fundamental!! Eu te levo para a fazer.\"\n\n\
      Ela te leva para se inscrever no torneio, e você faz a inscrição";
    }
    } else {
        prota.julia = 1;
        cout << "Garota:\"Você ai terinando!! Está afim de participar de um torneio de duelos aqui e amanhâ?\"\n\n\
        Você:\"VOCÊ DISSE DUELOS!? Obviamente, você parece até não saber com quem está falando\"\n\n\
        Júlia:\"QUE LEGALLLL! Esse torneio será incrível. Meu nome é Júlia, e o seu?\n\n\
        Você:\"" << prota.nome << ", e quero me inscrever nesse torneio imediatamente.\"\n\n\
        Ela te leva para se inscrever no torneio, e você faz a inscrição";
        prota.inscricao = 1;
        }

  cout << "\n\nVocê:\"Por feita a inscrição, agora, não que eu precise, vou trieinar, venha lutar sério comigo.\"\n\n\
  Júlia:\"Vamos, também preciso treinar. Mas primeiro irei ficar pelada naquele banheiro, espere um minuto.\"\n\n\
  Ela entra em uma sala:\n\n\
  0 > olhar pela fechadura\n\n\
  1 > fazer umas 100 flexões e alongamentos enquanto espera.\n\
  Act: ";
escolha2(act);
if(act == "0"){
cout << "Você olha pela fechadura da porta a ve com o explendor de seu belíssimo e monumental corpo em condições nuas enquanto ela se troca\n\n\
Ela sai com coupas de luta e fala:\n\n\
Júlia:\"Agora vamos trinar incansavelmente\"\n\n\
0 > \"Vamos lutar durante 6 horas sem parar\"\n\n\
1 > \"Eu ví você se trocando atravez da fechadura da porta\n\n";
escolha2(act);
if(act == "0"){
cout << "Vocês vão treinar, porém ela só leva surra já que você é muito mais forte que ela";
} else {
  prota.julia = 0;
  cout << "Ela fica envergonhada e vai embora. Você passa o resto do dia treinando com afinco e intensidade";
}
} else {
  cout << "Ela sai com roupas de treino:\n\n\
  Júlia:\"Uau, já está até treinando, como derrotar?\"\n\n\
  Você:\"Sim, agora vamos lutar durante 6 horas sem parar\"\n\n\
  Vocês vão treinar, porém ela só leva surra já que você é muito mais forte que ela.\n";

}
prota.torneio = 1;
cout << "Insira qualquer tecla:";
cin >> act;
}
}


///Casa dela--------------------------------------------------------------------------------------------------------------------
void casadajulia(personagem &prota, bool &horario, string act){
system("cls");
prota.julia = 1;
cout << "\n\n\nVocê e a sua vizinha vão até a casa da subrinha dela e tocam a campainha, após um tempo ela aparece na porta.\n\n\
vizinha:\"Oi júlia, meu vizinho maluco não quer mais sair da minha casa pedindo pelo cartão que você queria me dar\"\n\n\
Você:\"Sim, preciso do cartão\"\n\n\
Júlia:\"À essa hora? Eu pego para você, mas só por que quero que tenha muita gente participando.\"\n\n\
Ela traz o bilhete e fala: \"Aqui está, mas de onde vem todo esse interece, você não poderia falar comigo amanhã?\"\n\n\
Você:\"Não, não poderiamos correr o risco de não ter vaga para o elemento principal do evento\"\n\n\
Júlia:\"Uau, quer dizer que você quer competir? Nesse caso, vou te dar também uma ficha de inscrição. Basta que entregues\
ela para o monge Feijão.\"\n\n\
0 > Ir até o monge agora\n\n\
1 > Voltar para casa e ir no dia seguinte\n\
act:";
escolha2(act);
if(act == "0"){
  templo(prota, horario, act);
} else {
return;
}}


///início-----------------------------------------------------------------------------------------------------------------------
void introducao(personagem &prota, bool horario, string act){
 system("cls");
 cout << "\nVocê é um homem de 18 anos que mora na China e é fascinado por duelos. Seu nome é ('Digite um nome)': ";
 cin >> prota.nome;
 system("cls");
 cout << prota.nome << "\n Já são 22:30 e você está deitado em sua cama quando derrepente você ouve, vindo das paredes, alguém \
 falando a palavra \"duelo\".\n\n\
 Digite 0 > Se levantar para tentar ouvir melhor\n\
 Digite 1 > dormir\nact: ";
 escolha2(act);
 if(act == "0"){
   cout << "O som vem da casa de seus vizinhos, você se levanta, vai até as paredes, aproxima delas a sua orelha e ouve:\n\
   \"sim nada a ver esse negócio de duelo ai\"\n\
   0 > dormir\n\
   1 > ir na casa dela perguntar sobre o assunto\n\
   act: ";
   act = "a";
   escolha2(act);
   if(act == "1"){
        act = "a";
        cout << "Você sai de casa e vai até a porta da casa vizinha. Chegando lá, você bate na pota e ao ser atendido:\n\n\
        vizinha-\"Você à essa hora? Olá, " << prota.nome << ", o que veio fazer aqui?\"\n\n\
        você-\"Ouvi que estavam falando sobre duelos, então vim ver do que se tratava.\"\n\n\
        vizinha-\"E você também fica nos bisbilhotando é? Eu ein, vizinho maluco!\"\n\n\
        Ela começa a fechar a porta:\n\n\
        0 > deixar que ela feche e ir dormir\n\
        1 > impedí-la\n\
        act: ";

        escolha2(act);

        if(act == "1"){
                prota.vizinha = 0;
                act = "a";
          cout << "\nVocê pega a mão dela antes que a porta se feche, e a tira da massaneta.\n\n\
          vizinha:\"O que é isso!?\n\n\
          Assustada, ela novamente se move para fechar a porta, mas você impurra a porta quando a mão dela esta prestes\n\
         a tocá-la, fazendo com que ela agarrace em falso.\n\n\
          Você:\"Me conte o que te é sabido sobre duelos.\"\n\n\
          vizinha(assustada):\"Tenha calma, apenas ouvi que estão anunciando um campionato que terá no templo em breve\"\n\n\
          Você:\"O QUE!?!? Conte-me tudo o que sabes\"\n\n\
          vizinha:\"Não sei de nada, minha sobrinha é quem estava me oferecendo um bilhete, mas eu não quis pegar\"\n\n\
          Você:\"ONDE ELA ESTÁ?\"\n\n\
          vizinha:\"À essa hora ja está dormindo\"\n\n\
          0 > \"Tudo bem, amanhã vamos até lá\"\n\n\
          1 > \"Não é problema, eu posso acordar ela facilente\"\n\
          act: ";
          escolha2(act);
          }
          if(act == "1"){
            horario = 0;
            casadajulia(prota, horario, act);
          }


        } else {
        return;
        }

   } else {
   return;
   }
 return;
}

///Restaurante------------------------------------------------------------------------------------------------------------------
void restaurante(personagem &prota, string act){
    system("cls");
    prota.restaurante = 0;
    cout << "você\"Tenho que comer o quanto antes para ir treinar logooo!!\"\n\n\
    você vai até uma lanchonete, e um atendente o recebe;\n\n\
    Voce:\"Me dê a comida mais saldavel da casa.\"\n\n\
    Atendente:\"Ok, em dois minutos está pronta.\"\n\n\
    Você:\"DOIS MINUTOS!?!? você está louco? sabe com quem está lidando?\"\n\n\
    Atendente:\"Ora mas que pressa toda é essa? Não sei, quem é esse tal homem que lido agora?\"\n\n\
    Você:\"" << prota.nome << ", e preciso treinar imediatamente\n\
    Atendente:\"Vejo que se trata de um homem extraordinário, pego sua comida em 20 segundos, mas ela estará fria.\n\n\
    Você:\"Tudo bem, quente ou fria, eu te venceria num duelo de qualquer geito.\n\n\
    Atendente:\"Aqui está ^-^ são 8 reais.\n\n\
    0 > \"eu posso pagar 10.\"\n\n\
    1 > \"Ok, até mais\"\n\n\
    2 > \"Não pagarei nada\" e sair sem pagar\n\
    act: ";
    act = "a";
    while(act != "0" and act != "1" and act != "2"){
      cin >> act;
    if(act == "0"){
        prota.bolso = prota.bolso - 10;
    return;
    } else if(act == "1"){
    prota.bolso = prota.bolso - 8;
    } else {
    prota.atendente = 0;
    return;
    }
    }
}

///Homem dos jogos--------------------------------------------------------------------------------------------------------------
void homem(personagem &prota, string act){
system("cls");
srand(time(0));
int numero, numerodele, aposta=10000;
bool par=0, paresc=0;
cout << "Esse é um homem que fica todos os dias apostando par ou impar na mesma rua, seguno ele, por adquirir prática, \
ele tem mais chance de vencer do que perder.\n\n\
0 > Sair\n\
1 > Jogar\nact: ";
escolha2(act);
if(act == "0"){
    return;
} else {
    cout<<"R$" << prota.bolso << "\ncoloque uma quantia inteira para aposta: ";
    //não deixar apostar mais do que tem
   while(aposta > prota.bolso){
    cin >> aposta;
    }
cout << "\n0 > impar\n\
1 > par\n act: ";
escolha2(act);
if(act == "1"){
    paresc = 1;
}
cout << "escolha um número inteiro: ";
cin >> numero;
numerodele = rand() % 11;
//numeros de pariedade igual são pares, e diferentes são impares
if(numero % 2 == numerodele % 2){
    par = 1;
}
cout << "ele jogou " << numerodele << "\n";
if(par == paresc){
    cout << "Você ganhou + R$" << aposta;
} else {
    cout << "Você perdeu R$" << aposta;}
}
cout << "\ninsira qualquer tecla";
cin >> act;
return;
}

///Loja-------------------------------------------------------------------------------------------------------------------------
void loja(personagem &prota, string act){
    system("cls");
    prod azu;
    azu.nome = "sapatos azuis";
    azu.preco = 5;
    prod ama;
    ama.nome = "sapatos amarelados";
    ama.preco = 5;
    prod ele;
    ele.nome = "sapatos elegantes";
    ele.preco = 15;
    prod flo;
    flo.nome = "sapatos floridos";
    flo.preco = 30;
cout << "produtos:\n\n\
Você tem: " << prota.bolso << "\n\n\
0 > Sapato azul R$5\n\
1 > Sapato amarelo R$5\n\
2 > Sapato elegante R$15\n\
3 > Sapato florido R$30\n\
5 > Sair\n\
(Ao comprar um sapato novo você perde o atual)\n\
escolha: ";

  cin >> act;
  if(act == "0"){
    if(prota.bolso)
    if(prota.bolso >= azu.preco){
        prota.bolso = prota.bolso - 5;
        prota.sapato = "sapatos azuis";
        cout << "você comprou\n";
    }
  } else if(act == "1"){
      if(prota.bolso >= ama.preco){
        prota.sapato = "sapatos amarelados";
        prota.bolso = prota.bolso - 5;
        cout << "você comprou\n";
      }
  } else if(act == "2"){
    if(prota.bolso >= ele.preco){
      prota.sapato = "sapatos elegantes";
      prota.bolso = prota.bolso -15;
      cout << "você comprou\n";
    }
  } else if(act == "3"){
    if(prota.bolso >= flo.preco){
    prota.sapato = "sapatos floridos";
    prota.bolso = prota.bolso - 30;
    cout << "você comprou\n";
    }
  } else if(act == "5"){
  return;
  } else {
    cout << "\nVocê deseja comprar os sapatos secretos por todo o seu dinheiro -1?\n\n\
    1 > Sim\n\n\
    0 > Não\nact:";
    escolha2(act);
    if(act == "1"){
    prota.sapato = "sapatos secretos";
    prota.bolso = 1;
    cout << "você comprou\n";
    }
  }
  cout << "insira qualquer tecla: ";
  cin >> act;
return;
}//fecha função

///Floricultura------------------------------------------------------------------------------------------------------------------
void floricultura(personagem &prota, string act){
    ifstream arquivo;
    string frase;
    int atual;
    arquivo.open("file.txt");
    while(atual < 7){
            atual++;
        getline(arquivo,frase);
        cout << frase << "\n";
        if(atual == 2){
            cout << prota.bolso;
        }
    }
    arquivo.close();
    /*cout << "Floricultura:\n\n\
    Você tem: R$" << prota.bolso << "\n\n\
    0 > Rosa R$10\n\n\
    1 > Sair\nact:";*/
    escolha2(act);
    if(act == "0"){
            prota.bolso = prota.bolso - 10;
        cout << "para quem você quer entregar essa rosa?\n\n\
        0 > Vizinha\n\
        1 > Júlia\n\
        2 > Monge\n\
        3 > Atendente\n\
        4 > Homem do Par ou Impar\n\
        OUTRO > Ficar para sí\nact: ";
    cin >> act;
        if(act == "0"){
            prota.vizinha = 1;
        } else if(act == "1"){
          prota.julia = 1;}
        } else if(act == "2"){
        prota.monge = 1;
        } else if(act == "3"){
        prota.atendente = 1;
        } else if(act == "4"){
        prota.homem = 1;
        }
}

///Menu------------------------------------------------------------------------------------------------------------------------
int menu (personagem &prota, bool horario, string act){
  system("cls");
  act="a";
  cout << "Onde deseja ir\n";
  //filtro if para mostrar apenas os lugares disponíveis
  if(prota.restaurante){
    cout << "0 > Restaurante\n";
  }
  cout << "1 > Loja\n";
  cout << "2 > Floricultura\n";
  if(prota.templo){
    cout << "3 > Templo\n";
  } else {
    cout << "4 > Torneio\n";
  }
  cout << "5 > Homem jogos\n\
  act: \n";

//não permitir que o jogador entre onde ele ja foi
while(act != "0" and act != "1" and act != "2" and act != "3" and act != "4" and act != "5" and act != "6" and act != "7"){
    cin >> act;
    if(act == "0"){
        if(prota.restaurante){
            restaurante(prota, act);
        } else {
          cout << "Você não pode mais ir a esse local\nact: ";
          act = "a";
          }
    }
    if(act == "1"){
        loja(prota, act);
    }
    if(act =="2"){
        floricultura(prota, act);
    }
    if(act == "3"){
       if(prota.restaurante){
            cout << "você deve comer antes de ir para o templo.\nact: ";
            act = "a";
        } else {
          templo(prota, horario, act);
        }
    }
    if(act == "4"){
            if(prota.templo){
                cout << "O dia do torneio ainda não chegou\n";
                act = "a";
            } else {
        torneio(prota);
    }}
    if(act == "5"){
        homem(prota, act);
    }
}
}
int main(){
    setlocale(LC_ALL,"portuguese");
    cout << "\n\n" << endl;
    personagem prota;
    //1 = noite, 0 = dia
    bool horario = 1;
    string act="a";
    tela_de_inicio();
    introducao(prota, horario, act);
    horario = 0;
    while(prota.torneio){
        menu(prota, horario, act);
    }
    return 0;
}
