```mermaid
graph LR
subgraph Sistema SENOVA
A[Login Principal] --> B{Verificación de Rol};
B -- Credenciales Admin --> C[Dashboard Admin];
B -- Credenciales Docente --> D[Dashboard Docente];
B -- Credenciales Secretaria --> E[Dashboard Secretaria];

subgraph "Dashboard General"
C --> C1[Crear Usuario];
C --> C2[Lista de Usuarios];
C --> C3[Configurar Colegio];
C --> C4[Actualizar Datos];
C --> F{Módulo del Colegio};
C --> C6[Cerrar Sesión];

D --> D1[Actualizar Datos];
D --> F;
D --> D3[Cerrar Sesión];

E --> E1[Actualizar Datos];
E --> F;
E --> E3[Cerrar Sesión];
end

subgraph "Módulo del Colegio"
F --> G[Login Secundario];
G --> H[Dashboard Interno];

subgraph "Sidebar (Acceso por Rol)"
H --> I{Gestión de Estudiantes};
H --> J[Estudiantes Secretaría];
H --> K{Asignaturas};
H --> L[Cursos];
H --> M[Cerrar Sesión del Módulo];
end
end

subgraph "Permisos del Sidebar"
C -- Admin --> I;
C -- Admin --> J;
C -- Admin --> K;
C -- Admin --> L;
C -- Admin --> M;

D -- Docente --> I;
D -- Docente --> M;

E -- Secretaria --> J;
E -- Secretaria --> K;
E -- Secretaria --> L;
E -- Secretaria --> M;
end

subgraph "Detalle Submódulos"
I --> I1[Estudiantes CRUD];
I --> I2[Matrículas CRUD];
I -->|Asistencias| I3[Asistencias CRUD];
I -->|Reportes| I4[Boletín Académico];

K --> K1[Primaria];
K --> K2[Secundaria];
end

%% Estilos para claridad
style A fill:#242738,stroke:#fff,stroke-width:2px,color:#fff
style F fill:#325472,stroke:#fff,stroke-width:2px,color:#fff
style G fill:#325472,stroke:#fff,stroke-width:2px,color:#fff
```