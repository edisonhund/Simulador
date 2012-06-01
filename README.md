////////////////////////////////main///////////////////////

using namespace std;
Relogio* Relogio::instancia = 0;
/*
 * 
 */
int main(int argc, char** argv) {

    
    list<Evento> eventos;
    Evento* e;
    Estatistica estatistica;
    
    while(!eventos.empty())
    {
  e = &eventos.front();
      e->executa();
        Relogio::getInstancia()->setValor(e->duracao);
    }
    estatistica.show();
    
    return 0;
}

///////////////////Relogio.h//////////////////////////////

class Relogio {
   
  private:  
    static Relogio *instancia;

  public:
    int intervalo; 
    int tempo;
    
    int getValor();
    int getIntervalo();
    void setIntervalo(int);
    
    void setValor(int);
    
    static Relogio *getInstancia(){
        if (!instancia)
          instancia = new Relogio;
        return instancia;
    }    
    
    Relogio();
   
    void contaTempo(int);

};

//////////////Relogio.cpp////////////////////////////

Relogio::Relogio(){
    this->intervalo = 0;
    this->tempo = 0;
}

void Relogio::setValor(int x){
    this->tempo = x; 
}

void Relogio::setIntervalo(int x){
    this->intervalo = x;
}

void Relogio::contaTempo(int x){
     this->tempo += x;
 
}

int Relogio::getValor(){
        return tempo;
    }

int Relogio::getIntervalo(){
        return intervalo;
    }
    
///////////////Evento.cpp/////////////////////////////////

Evento::Evento(int data, int duracao, int desvio)
{
    this->data = data;
    this->duracao = duracao;
    this->desvio = desvio;
}

int Evento::getData() {
    return data;
}

int Evento::getDuracao() {
    return duracao;
}

int Evento::getDesvio() {
    return desvio;
}

void Evento::setData(int data) {
    this->data = data;
}

void Evento::setDuracao(int duracao) {
    this->duracao = duracao;
}

void Evento::setDesvio(int desvio) {
    this->desvio = desvio;
}

void Evento::executa(){
    
}

//////////////////////Evento.h////////////////////////

class Evento {
public:
    int data;
    int duracao;
    int desvio;
    Evento(int data=0, int duracao=0, int desvio=0);
    Evento();
    virtual ~Evento();

    int getData();
    int getDuracao();
    int getDesvio();

    void setData(int);
    void setDuracao(int);
    void setDesvio(int);

    virtual void executa();

};