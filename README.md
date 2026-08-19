# IFCoffeInsight

                 ☕ COFFEEINSIGHT
                       │
        ┌──────────────┼──────────────┐
        │              │              │
     PRODUÇÃO       QUALIDADE       VENDA
        │              │              │


```Python
// O material.dart importa  componentes do Flutter Material
import 'package:flutter/material.dart';

// Quero utilizar os elementos/ ou componentes que foram criados no  producao_page
import 'pages/producao_page.dart';

void main() {
  // Ponto de entrada do programa
  runApp(const CoffeInsight());
}

class CoffeInsight extends StatelessWidget {
  const CoffeInsight({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(  // Container principal da aplicação que permite configurar
      // tema; navegação; título; rotas;  localização e  tela inicial.
      debugShowCheckedModeBanner: false,

      title: 'CaféTech',

      theme: ThemeData(
        useMaterial3: true,

        colorScheme: ColorScheme.fromSeed(
          seedColor: const Color(0xFF6F4E37),
        ),

        scaffoldBackgroundColor:
        const Color(0xFFF8F5F0),

        appBarTheme: const AppBarTheme(
          centerTitle: false,
          elevation: 0,
        ),
      ),

      home: const ProducaoPage(),
    );
  }
}
```


```Python
import 'package:flutter/material.dart';

import 'qualidade_page.dart';

class ProducaoPage extends StatelessWidget {
  const ProducaoPage({super.key});

  final int arabica = 850;
  final int robusta = 420;

  @override
  Widget build(BuildContext context) {
    final int total = arabica + robusta;

    return Scaffold( // Representa a estrutura visual da Tela padronizada pelo google
      appBar: AppBar(
        title: const Row(
          children: [
            Icon(Icons.coffee),
            SizedBox(width: 8),
            Text(
              'CafeInsight',
              style: TextStyle(
                fontWeight: FontWeight.bold,
              ),
            ),
          ],
        ),
      ),

      body: SafeArea(
        child: SingleChildScrollView(
          padding: const EdgeInsets.all(20),

          child: Column(
            crossAxisAlignment:
            CrossAxisAlignment.start,

            children: [

              // CABEÇALHO
              const Text(
                'Olá, produtor! 👋',
                style: TextStyle(
                  fontSize: 28,
                  fontWeight: FontWeight.bold,
                ),
              ),

              const SizedBox(height: 8),

              Text(
                'Acompanhe sua produção de café.',
                style: TextStyle(
                  fontSize: 16,
                  color: Colors.grey.shade600,
                ),
              ),

              const SizedBox(height: 25),

              // CARDS DE PRODUÇÃO
              Row(
                children: [

                  Expanded(
                    child: _CafeCard(
                      tipo: 'Arábica',
                      sacas: arabica,
                      icone: Icons.coffee,
                    ),
                  ),

                  const SizedBox(width: 15),

                  Expanded(
                    child: _CafeCard(
                      tipo: 'Robusta',
                      sacas: robusta,
                      icone: Icons.local_cafe,
                    ),
                  ),
                ],
              ),

              const SizedBox(height: 20),

              // TOTAL
              Container(
                width: double.infinity,

                padding: const EdgeInsets.all(20),

                decoration: BoxDecoration(
                  color: const Color(0xFF6F4E37),
                  borderRadius:
                  BorderRadius.circular(20),
                ),

                child: Column(
                  crossAxisAlignment:
                  CrossAxisAlignment.start,

                  children: [

                    const Text(
                      'Produção total',
                      style: TextStyle(
                        color: Colors.white70,
                        fontSize: 15,
                      ),
                    ),

                    const SizedBox(height: 8),

                    Text(
                      '$total sacas',
                      style: const TextStyle(
                        color: Colors.white,
                        fontSize: 32,
                        fontWeight: FontWeight.bold,
                      ),
                    ),

                    const SizedBox(height: 5),

                    const Text(
                      'Arábica + Robusta',
                      style: TextStyle(
                        color: Colors.white70,
                      ),
                    ),
                  ],
                ),
              ),

              const SizedBox(height: 30),

              const Text(
                'Próximo passo',
                style: TextStyle(
                  fontSize: 20,
                  fontWeight: FontWeight.bold,
                ),
              ),

              const SizedBox(height: 12),

              // BOTÃO DE NAVEGAÇÃO
              SizedBox(
                width: double.infinity,
                height: 60,

                child: ElevatedButton(
                  onPressed: () {

                    Navigator.push(
                      context,

                      MaterialPageRoute(
                        builder: (context) =>
                        const QualidadePage(),
                      ),
                    );

                  },

                  child: const Row(
                    mainAxisAlignment:
                    MainAxisAlignment.center,

                    children: [

                      Icon(Icons.star),

                      SizedBox(width: 10),

                      Text(
                        'Avaliar qualidade',
                        style: TextStyle(
                          fontSize: 17,
                          fontWeight: FontWeight.bold,
                        ),
                      ),

                      SizedBox(width: 10),

                      Icon(
                        Icons.arrow_forward,
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ),
      ),
    );
  }
}

class _CafeCard extends StatelessWidget {

  final String tipo;
  final int sacas;
  final IconData icone;

  const _CafeCard({
    required this.tipo,
    required this.sacas,
    required this.icone,
  });

  @override
  Widget build(BuildContext context) {

    return Card(
      elevation: 0,

      shape: RoundedRectangleBorder(
        borderRadius: BorderRadius.circular(20),
      ),

      child: Padding(
        padding: const EdgeInsets.all(18),

        child: Column(
          crossAxisAlignment:
          CrossAxisAlignment.start,

          children: [

            Container(
              width: 45,
              height: 45,

              decoration: BoxDecoration(
                color: const Color(0xFFF0E6DD),
                borderRadius:
                BorderRadius.circular(12),
              ),

              child: Icon(
                icone,
                color: const Color(0xFF6F4E37),
              ),
            ),

            const SizedBox(height: 20),

            Text(
              '$sacas',
              style: const TextStyle(
                fontSize: 28,
                fontWeight: FontWeight.bold,
              ),
            ),

            const SizedBox(height: 3),

            const Text(
              'sacas',
              style: TextStyle(
                color: Colors.grey,
              ),
            ),

            const SizedBox(height: 8),

            Text(
              tipo,
              style: const TextStyle(
                fontSize: 16,
                fontWeight: FontWeight.w600,
              ),
            ),
          ],
        ),
      ),
    );
  }
}



```



