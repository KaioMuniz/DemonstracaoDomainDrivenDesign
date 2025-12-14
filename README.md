```

src/main/java/br/com/kaiomuniz
│
├── domain                     # Núcleo do negócio (DDD puro)
│   ├── aggregates             # Aggregate Roots e limites de consistência do domínio
│   ├── entities               # Entidades com identidade e regras de negócio
│   ├── valueobjects           # Objetos de valor imutáveis (sem identidade)
│   ├── repositories           # Contratos (interfaces) de persistência do domínio
│   ├── services               # Serviços de domínio (regras que não cabem em entidades)
│   ├── events                 # Eventos de domínio (algo importante aconteceu)
│   ├── specifications         # Regras, critérios e validações reutilizáveis do domínio
│   └── exceptions             # Exceções específicas de regras de negócio
│
├── application                # Camada de casos de uso (orquestração)
│   ├── usecases               # Intenções do sistema (ações que o usuário pode executar)
│   │   ├── commands           # Casos de uso de escrita (criar, alterar, excluir)
│   │   ├── queries            # Casos de uso de leitura (consultas, sem alterar estado)
│   │   └── handlers           # Executores dos commands e queries (coordenação)
│   ├── services               # Serviços de aplicação (coordenação entre use cases)
│   ├── ports                  # Interfaces de comunicação (Hexagonal)
│   │   ├── in                 # Portas de entrada (o que a aplicação expõe)
│   │   └── out                # Portas de saída (o que a aplicação precisa de fora)
│   └── dtos                   # DTOs internos da aplicação (não são HTTP)
│
├── infrastructure             # Detalhes técnicos e implementações concretas
│   ├── persistence            # Tudo relacionado à persistência de dados
│   │   ├── jpa                # Implementação específica com JPA/Hibernate
│   │   │   ├── entities       # Entidades JPA (mapeamento ORM)
│   │   │   └── repositories   # Repositórios JPA (Spring Data / Hibernate)
│   │   └── mappers            # Conversão entre domínio ↔ persistência
│   ├── messaging              # Comunicação assíncrona / eventos
│   │   ├── producers          # Publicadores de mensagens/eventos
│   │   └── consumers          # Consumidores de mensagens/eventos
│   ├── external               # Integração com sistemas externos
│   │   ├── clients            # Clientes HTTP / REST / APIs externas
│   │   └── adapters           # Adaptadores que traduzem o externo para o domínio
│   ├── security               # Segurança (auth, JWT, filtros, interceptors)
│   └── config                 # Configurações técnicas (beans, properties, setup)
│
├── presentation               # Camada de entrada e saída (interface com o usuário)
│   ├── controllers            # Controllers REST (HTTP → Application)
│   ├── dtos                   # DTOs específicos da camada HTTP
│   │   ├── request            # DTOs de entrada (payloads HTTP)
│   │   └── response           # DTOs de saída (respostas HTTP)
│   ├── mappers                # Conversão DTO HTTP ↔ DTO Application
│   └── handlers               # Tratamento de erros e exceções (ControllerAdvice)
│
└── shared                     # Código compartilhado entre domínios
    ├── utils                  # Utilitários genéricos (datas, strings, helpers)
    ├── constants              # Constantes globais (evita magic values)
    ├── exceptions             # Exceções técnicas compartilhadas
    └── annotations            # Anotações customizadas (cross-cutting concerns)


```
