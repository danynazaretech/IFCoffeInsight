# IFCoffeInsight

                 ☕ COFFEEINSIGHT
                       │
        ┌──────────────┼──────────────┐
        │              │              │
     PRODUÇÃO       QUALIDADE       VENDA
        │              │              │


    ```Flutter
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

  ```
}
    ```
