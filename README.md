# Crie-seu-Gerenciador-de-Salas-de-Reuni-es-com-Java-e-Angular

Vamos dividir o projeto em módulos, começando pela API com Spring Boot e depois o front-end com Angular.

### Módulo 1: API Spring Boot para Gerenciamento de Salas de Reunião
**Descrição:**
Desenvolveremos uma API RESTful usando Spring Boot, que permitirá aos usuários criar, listar, atualizar e deletar informações de salas de reunião.

**Tecnologias:**
- **Spring Boot**: Para a criação da aplicação e exposição da API.
- **Spring Data JPA**: Para a persistência de dados e operações CRUD.
- **H2 Database**: Um banco de dados em memória para facilitar o desenvolvimento e testes.

**Exemplo de código - Classe SalaDeReuniao:**
```java
@Entity
public class SalaDeReuniao {
    @Id
    @GeneratedValue(strategy = GenerationType.AUTO)
    private Long id;
    private String nome;
    private String data;
    private String inicioHorario;
    private String fimHorario;

    // Getters e Setters
}
```

**Exemplo de código - Controller:**
```java
@RestController
@RequestMapping("/api/salas")
public class SalaDeReuniaoController {

    @Autowired
    private SalaDeReuniaoRepository repository;

    // Métodos para CRUD
}
```

### Módulo 2: Front-end SPA com Angular
**Descrição:**
Criaremos uma Single Page Application (SPA) usando Angular que consumirá a API Spring Boot para exibir e gerenciar as salas de reunião.

**Tecnologias:**
- **Angular**: Framework para construir o front-end.
- **Angular CLI**: Para gerar componentes, serviços e outras funcionalidades.
- **RxJS**: Para manipulação de eventos assíncronos e streams de dados.

**Exemplo de código - Serviço Angular:**
```typescript
@Injectable({
  providedIn: 'root'
})
export class SalaDeReuniaoService {
  private apiUrl = 'http://localhost:8080/api/salas';

  constructor(private http: HttpClient) { }

  // Métodos para consumir a API
}
```

**Exemplo de código - Componente Angular:**
```typescript
@Component({
  selector: 'app-sala-list',
  templateUrl: './sala-list.component.html',
  styleUrls: ['./sala-list.component.css']
})
export class SalaListComponent implements OnInit {
  salas: SalaDeReuniao[];

  constructor(private salaService: SalaDeReuniaoService) { }

  ngOnInit() {
    this.salaService.getSalas().subscribe(
      (data: SalaDeReuniao[]) => {
        this.salas = data;
      },
      (error) => {
        console.log(error);
      }
    );
  }
}
```

Esses são apenas exemplos básicos para começar. Cada parte do código deve ser expandida com mais funcionalidades conforme as necessidades do projeto. Lembre-se de testar cada parte do sistema extensivamente e de seguir as melhores práticas de desenvolvimento de software.
