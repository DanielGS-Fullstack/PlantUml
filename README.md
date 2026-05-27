# PlantUml
test UML
@startuml
skinparam componentStyle rectangle
skinparam shadowing false
skinparam packageStyle rectangle
skinparam monochrome true
skinparam defaultFontName Arial

title Sistema HJK - Diagrama de Componentes

actor Paciente
actor Recepcionista
actor Enfermeiro
actor Médico
actor Administrador

package "Sistema HJK" {

    component "Agendamento Online" as AG {
        [Marcação de Consultas]
    }

    component "Check-in e Cadastro" as CK {
        [Validação de Convênios]
        [Controle de Entrada]
    }

    component "Triagem e\nClassificação de Risco" as TR {
        [Registro de Sinais Vitais]
        [Classificação de Prioridade]
    }

    component "Prontuário Eletrônico\n do Paciente (PEP)" as PEP {
        [Histórico Clínico]
        [Dados do Paciente]
    }

    component "Gestão de Exames" as EX {
        [Solicitação de Exames]
        [Integração Laboratorial]
        [Laudos em Tempo Real]
    }

    component "Prescrição Digital" as PR {
        [Receitas]
        [Medicamentos]
        [Assinatura Digital]
    }

    component "Emissão de Documentos" as DOC {
        [Atestados]
        [Encaminhamentos]
        [Assinatura Digital]
    }

    component "Controle de Acesso\n(RBAC)" as RBAC {
        [Permissões por Perfil]
    }

    component "Trilha de Auditoria" as AUD {
        [Logs Imutáveis]
        [Registro de Acessos]
    }

    component "Gerenciamento\nAdministrativo" as ADM {
        [Usuários]
        [Relatórios]
        [Permissões]
    }
}

' Relação dos atores
Paciente --> AG
Recepcionista --> CK
Enfermeiro --> TR
Médico --> PEP
Administrador --> ADM
Administrador --> AUD

' Fluxo principal
AG --> CK
CK --> TR
TR --> PEP

' Integração entre módulos
PEP --> EX
PEP --> PR
PEP --> DOC

' Segurança
EX --> RBAC
PR --> RBAC
DOC --> RBAC
PEP --> RBAC

RBAC --> AUD
AUD --> ADM

note bottom
Figura 1 – Diagrama de Componentes do Sistema HJK
Fonte: Elaboração própria.
end note

@enduml
