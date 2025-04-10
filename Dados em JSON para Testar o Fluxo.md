# Dados em JSON para Testar o Fluxo Completo da API

Aqui estão os dados em JSON para testar o fluxo completo da API, organizados na sequência correta de operações:

## 1. Criar Especialidades

### Especialidade 1: Cardiologia
```json
{
  "nome": "Cardiologia",
  "descricao": "Tratamento de doenças relacionadas ao coração e sistema circulatório"
}
```

### Especialidade 2: Neurologia
```json
{
  "nome": "Neurologia",
  "descricao": "Tratamento de doenças relacionadas ao sistema nervoso"
}
```

### Especialidade 3: Ortopedia
```json
{
  "nome": "Ortopedia",
  "descricao": "Tratamento de doenças relacionadas aos ossos e articulações"
}
```

## 2. Criar Médicos

### Médico 1: Dr. Carlos Silva
```json
{
  "nome": "Dr. Carlos Silva",
  "crm": "123456",
  "email": "carlos.silva@hospital.com",
  "telefone": "11999998888",
  "especialidadeIds": [1, 2]
}
```

### Médico 2: Dra. Ana Santos
```json
{
  "nome": "Dra. Ana Santos",
  "crm": "654321",
  "email": "ana.santos@hospital.com",
  "telefone": "11988887777",
  "especialidadeIds": [3]
}
```

## 3. Criar Pacientes

### Paciente 1: João Pereira
```json
{
  "nome": "João Pereira",
  "cpf": "12345678901",
  "dataNascimento": "1980-05-10",
  "email": "joao.pereira@email.com",
  "telefone": "11977776666",
  "endereco": "Rua das Flores, 123 - São Paulo/SP"
}
```

### Paciente 2: Maria Oliveira
```json
{
  "nome": "Maria Oliveira",
  "cpf": "98765432109",
  "dataNascimento": "1992-08-15",
  "email": "maria.oliveira@email.com",
  "telefone": "11966665555",
  "endereco": "Av. Paulista, 1000 - São Paulo/SP"
}
```

## 4. Agendar Consultas

### Consulta 1: João com Dr. Carlos (agendada para futuro)
```json
{
  "dataHora": "2025-04-15T14:00:00",
  "status": "AGENDADA",
  "medicoId": 1,
  "pacienteId": 1,
  "observacao": "Primeira consulta - Avaliação cardiovascular"
}
```

### Consulta 2: Maria com Dra. Ana (agendada para hoje)
```json
{
  "dataHora": "2025-04-08T15:30:00",
  "status": "AGENDADA",
  "medicoId": 2,
  "pacienteId": 2,
  "observacao": "Consulta para avaliação de dor no joelho"
}
```

## 5. Marcar Consulta como Realizada (PUT para /consultas/{id}/realizar)

Use o endpoint `/consultas/2/realizar` para marcar a consulta 2 como realizada.

## 6. Criar Prontuário para Consulta Realizada

```json
{
  "consultaId": 2,
 "anamnese": "Paciente relata dor no joelho direito há 2 semanas após queda durante atividade esportiva. Refere dor ao caminhar e dificuldade para flexionar o joelho.",
  "diagnostico": "Suspeita de lesão no ligamento colateral medial do joelho direito",
  "planoTratamento": "Repouso relativo por 2 semanas, aplicação de gelo local, anti-inflamatórios não esteroidais e encaminhamento para fisioterapia",
  "dataCriacao": "2022-03-10T12:15:50",
  "dataAtualizacao": "2022-03-10T12:15:50"
}
```

## 7. Criar Receitas para Consulta Realizada

### Receita 1: Anti-inflamatório
```json
{
    "consultaId": 2,
  "medicamento": "Ibuprofeno 600mg",
  "posologia": "Tomar 1 comprimido a cada 8 horas por 5 dias",
  "observacoes": "Tomar após as refeições para evitar irritação gástrica",
  "dataValidade": "2025-05-08T23:59:59",
  "dataEmissao": "2022-03-10T12:15:50"
}
```

### Receita 2: Analgésico
```json
{
  "consultaId": 2,
  "medicamento": "Paracetamol 750mg",
  "posologia": "Tomar 1 comprimido a cada 6 horas em caso de dor, não excedendo 4 comprimidos por dia",
  "observacoes": "Suspender uso e entrar em contato caso a dor persista por mais de 3 dias",
  "dataValidade": "2025-05-08T23:59:59",
  "dataEmissao": "2022-03-10T12:15:50"
}
```

## 8. Solicitar Exames para Consulta Realizada

### Exame 1: Ressonância Magnética
```json
{
 "consultaId": 2,
  "nome": "Ressonância Magnética de Joelho Direito",
  "tipo": "IMAGEM",
  "instrucoes": "Jejum não necessário. Remover objetos metálicos. Informar uso de implantes ou marcapassos.",
  "dataSolicitacao": "2022-03-10T12:15:50",
  "dataResultado": "2022-03-10T12:15:50",
  "resultado": "string"
}
```

### Exame 2: Raio-X
```json
{
 "consultaId": 2,
  "nome": "Raio-X do Joelho Direito (AP e Perfil)",
  "tipo": "IMAGEM",
  "instrucoes": "Não necessita preparo específico.",
  "dataSolicitacao": "2022-03-10T12:15:50",
   "dataResultado": "2022-03-10T12:15:50",
  "resultado": "string"
}
```

## 9. Registrar Resultado de Exame (PUT para /exames/{id}/resultado)

Use o endpoint `/exames/1/resultado?resultado=Imagem de ressonância magnética evidencia edema no ligamento colateral medial com ruptura parcial de fibras. Sem alterações em meniscos. Discreta efusão articular.`

Use o endpoint `/exames/2/resultado?resultado=Radiografia sem evidência de fratura ou luxação. Discreto aumento de partes moles.`

## 10. Cancelar Consulta (opcional)

Use o endpoint `/consultas/1/cancelar` para cancelar a consulta futura.

## Fluxo de Teste:

1. Criar especialidades (POST /especialidades)
2. Criar médicos (POST /medicos)
3. Criar pacientes (POST /pacientes)
4. Agendar consultas (POST /consultas)
5. Marcar a consulta 2 como realizada (PUT /consultas/2/realizar)
6. Criar prontuário (POST /prontuarios)
7. Criar receitas (POST /receitas)
8. Solicitar exames (POST /exames)
9. Registrar resultados dos exames (PUT /exames/{id}/resultado)
10. (Opcional) Cancelar a consulta 1 (PUT /consultas/1/cancelar)

Depois de cada etapa, você pode usar as requisições GET correspondentes para verificar se os dados foram salvos corretamente