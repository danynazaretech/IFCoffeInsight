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





``` Python
import 'package:flutter/material.dart';

import 'venda_page.dart';

class QualidadePage extends StatefulWidget {
  const QualidadePage({super.key});

  @override
  State<QualidadePage> createState() =>
      _QualidadePageState();
}

class _QualidadePageState
    extends State<QualidadePage> {

  final TextEditingController notaController =
  TextEditingController();

  int nota = 0;

  String get classificacao {

    if (nota >= 85) {
      return 'Especial';
    }

    if (nota >= 70) {
      return 'Superior';
    }

    return 'Comercial';
  }

  IconData get icone {

    if (nota >= 85) {
      return Icons.star;
    }

    if (nota >= 70) {
      return Icons.thumb_up;
    }

    return Icons.coffee;
  }

  void calcular() {

    setState(() {

      nota =
          int.tryParse(
            notaController.text,
          ) ?? 0;

    });
  }

  @override
  Widget build(BuildContext context) {

    return Scaffold(

      appBar: AppBar(
        title: const Text(
          'Qualidade',
        ),
      ),

      body: SafeArea(

        child: SingleChildScrollView(

          padding: const EdgeInsets.all(20),

          child: Column(

            crossAxisAlignment:
            CrossAxisAlignment.start,

            children: [

              const Text(
                '⭐',
                style: TextStyle(
                  fontSize: 45,
                ),
              ),

              const SizedBox(height: 10),

              const Text(
                'Avaliação do café',
                style: TextStyle(
                  fontSize: 28,
                  fontWeight: FontWeight.bold,
                ),
              ),

              const SizedBox(height: 8),

              Text(
                'Digite a nota obtida na prova de '
                    'xícara.',
                style: TextStyle(
                  color: Colors.grey.shade600,
                  fontSize: 16,
                ),
              ),

              const SizedBox(height: 30),

              TextField(

                controller: notaController,

                keyboardType:
                TextInputType.number,

                decoration:
                InputDecoration(

                  labelText:
                  'Nota do café',

                  hintText:
                  'Ex.: 86',

                  prefixIcon:
                  const Icon(
                    Icons.star,
                  ),

                  border:
                  OutlineInputBorder(
                    borderRadius:
                    BorderRadius.circular(16),
                  ),
                ),
              ),

              const SizedBox(height: 15),

              SizedBox(

                width: double.infinity,
                height: 55,

                child: ElevatedButton.icon(

                  onPressed: calcular,

                  icon: const Icon(
                    Icons.calculate,
                  ),

                  label: const Text(
                    'Calcular qualidade',
                    style: TextStyle(
                      fontSize: 16,
                    ),
                  ),
                ),
              ),

              const SizedBox(height: 30),

              // RESULTADO
              Container(

                width: double.infinity,

                padding:
                const EdgeInsets.all(25),

                decoration:
                BoxDecoration(

                  borderRadius:
                  BorderRadius.circular(24),

                  border: Border.all(
                    color: Colors.grey.shade300,
                  ),

                  color: Colors.white,
                ),

                child: Column(

                  children: [

                    Icon(
                      icone,
                      size: 55,
                      color:
                      const Color(0xFF6F4E37),
                    ),

                    const SizedBox(height: 15),

                    Text(
                      '$nota pontos',
                      style: const TextStyle(
                        fontSize: 34,
                        fontWeight: FontWeight.bold,
                      ),
                    ),

                    const SizedBox(height: 5),

                    Text(
                      classificacao,
                      style: const TextStyle(
                        fontSize: 22,
                        fontWeight: FontWeight.w600,
                      ),
                    ),
                  ],
                ),
              ),

              const SizedBox(height: 30),

              SizedBox(

                width: double.infinity,
                height: 55,

                child: ElevatedButton.icon(

                  onPressed: () {

                    Navigator.push(
                      context,

                      MaterialPageRoute(
                        builder: (context) {
                         return VendaPage(
                           notaQualidade: nota,
                         );
                        },
                      ),
                    );

                  },

                  icon: const Icon(
                    Icons.attach_money,
                  ),

                  label: const Text(
                    'Registrar venda',
                    style: TextStyle(
                      fontSize: 16,
                    ),
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
```
```Python 
import 'package:flutter/material.dart';

class VendaPage extends StatefulWidget {
  // ============================================================
  // DADO RECEBIDO DA TELA DE QUALIDADE
  // ============================================================

  final int notaQualidade;

  const VendaPage({
    super.key,
    required this.notaQualidade,
  });

  @override
  State<VendaPage> createState() => _VendaPageState();
}

// ================================================================
// STATE DA TELA
// ================================================================

class _VendaPageState extends State<VendaPage> {

  // ============================================================
  // CONTROLLERS
  // ============================================================

  final precoController = TextEditingController();
  final freteController = TextEditingController();
  final armazenagemController = TextEditingController();
  final taxasController = TextEditingController();

  // ============================================================
  // VARIÁVEIS DE ESTADO
  // ============================================================

  double precoVenda = 0;
  double frete = 0;
  double armazenagem = 0;
  double taxas = 0;

  // ============================================================
  // GETTERS
  // ============================================================

  // Soma todos os custos logísticos
  double get custoLogistica {
    return frete + armazenagem + taxas;
  }

  // Valor que sobra para o produtor
  double get valorProdutor {
    return precoVenda - custoLogistica;
  }

  // Percentual do valor da venda gasto com logística
  double get percentualLogistica {

    if (precoVenda == 0) {
      return 0;
    }

    return (custoLogistica / precoVenda) * 100;
  }

  // Classificação recebida da tela anterior
  String get classificacao {

    if (widget.notaQualidade >= 85) {
      return 'Especial';
    }

    if (widget.notaQualidade >= 70) {
      return 'Superior';
    }

    return 'Comercial';
  }

  // Mensagem automática sobre a logística
  String get mensagemAnalise {

    if (precoVenda == 0) {
      return 'Informe os valores da venda para realizar a análise.';
    }

    if (percentualLogistica > 20) {
      return 'Os custos logísticos estão elevados.';
    }

    if (percentualLogistica > 10) {
      return 'Os custos logísticos estão moderados.';
    }

    return 'Os custos logísticos estão controlados.';
  }

  // ============================================================
  // MÉTODO PARA CALCULAR
  // ============================================================

  void calcular() {

    setState(() {

      precoVenda =
          double.tryParse(
            precoController.text.replaceAll(',', '.'),
          ) ?? 0;

      frete =
          double.tryParse(
            freteController.text.replaceAll(',', '.'),
          ) ?? 0;

      armazenagem =
          double.tryParse(
            armazenagemController.text.replaceAll(',', '.'),
          ) ?? 0;

      taxas =
          double.tryParse(
            taxasController.text.replaceAll(',', '.'),
          ) ?? 0;
    });
  }

  // ============================================================
  // WIDGET REUTILIZÁVEL PARA CAMPOS
  // ============================================================

  Widget campo(
      String label,
      IconData icon,
      TextEditingController controller,
      ) {

    return TextField(

      controller: controller,

      keyboardType:
      const TextInputType.numberWithOptions(
        decimal: true,
      ),

      decoration: InputDecoration(

        labelText: label,

        prefixIcon: Icon(icon),

        prefixText: 'R\$ ',

        border: OutlineInputBorder(
          borderRadius:
          BorderRadius.circular(16),
        ),

        focusedBorder: OutlineInputBorder(
          borderRadius:
          BorderRadius.circular(16),

          borderSide: const BorderSide(
            width: 2,
          ),
        ),
      ),
    );
  }

  // ============================================================
  // BUILD
  // ============================================================

  @override
  Widget build(BuildContext context) {

    return Scaffold(

      appBar: AppBar(

        title: const Text(
          'Venda do café',
        ),
      ),

      body: SafeArea(

        child: SingleChildScrollView(

          padding:
          const EdgeInsets.all(20),

          child: Column(

            crossAxisAlignment:
            CrossAxisAlignment.start,

            children: [

              // ==================================================
              // CABEÇALHO
              // ==================================================

              const Text(
                '💰',
                style: TextStyle(
                  fontSize: 45,
                ),
              ),

              const SizedBox(
                height: 10,
              ),

              const Text(
                'Simule sua venda',
                style: TextStyle(
                  fontSize: 28,
                  fontWeight:
                  FontWeight.bold,
                ),
              ),

              const SizedBox(
                height: 8,
              ),

              Text(
                'Descubra quanto realmente '
                    'chega ao bolso do produtor.',
                style: TextStyle(
                  fontSize: 16,
                  color:
                  Colors.grey.shade600,
                ),
              ),

              const SizedBox(
                height: 25,
              ),

              // ==================================================
              // CARD DA QUALIDADE
              // ==================================================

              Card(

                elevation: 0,

                color:
                Colors.orange.shade50,

                shape:
                RoundedRectangleBorder(
                  borderRadius:
                  BorderRadius.circular(20),

                  side: BorderSide(
                    color:
                    Colors.orange.shade200,
                  ),
                ),

                child: Padding(

                  padding:
                  const EdgeInsets.all(18),

                  child: Row(

                    children: [

                      Container(

                        width: 55,
                        height: 55,

                        decoration:
                        BoxDecoration(
                          color:
                          Colors.orange.shade100,

                          shape:
                          BoxShape.circle,
                        ),

                        child: Icon(
                          Icons.star,
                          color:
                          Colors.orange.shade800,
                          size: 30,
                        ),
                      ),

                      const SizedBox(
                        width: 15,
                      ),

                      Expanded(

                        child: Column(

                          crossAxisAlignment:
                          CrossAxisAlignment.start,

                          children: [

                            const Text(
                              'Qualidade do café',
                              style: TextStyle(
                                fontSize: 14,
                                color:
                                Colors.black54,
                              ),
                            ),

                            const SizedBox(
                              height: 4,
                            ),

                            Text(
                              '${widget.notaQualidade} pontos',
                              style:
                              const TextStyle(
                                fontSize: 21,
                                fontWeight:
                                FontWeight.bold,
                              ),
                            ),

                            const SizedBox(
                              height: 2,
                            ),

                            Text(
                              classificacao,
                              style: TextStyle(
                                color:
                                Colors.orange.shade800,
                                fontWeight:
                                FontWeight.bold,
                              ),
                            ),
                          ],
                        ),
                      ),
                    ],
                  ),
                ),
              ),

              const SizedBox(
                height: 30,
              ),

              // ==================================================
              // PREÇO
              // ==================================================

              const Text(
                '💵 Valor da venda',
                style: TextStyle(
                  fontSize: 18,
                  fontWeight:
                  FontWeight.bold,
                ),
              ),

              const SizedBox(
                height: 12,
              ),

              campo(
                'Preço de venda',
                Icons.attach_money,
                precoController,
              ),

              const SizedBox(
                height: 25,
              ),

              // ==================================================
              // CUSTOS
              // ==================================================

              const Text(
                '🚚 Custos logísticos',
                style: TextStyle(
                  fontSize: 18,
                  fontWeight:
                  FontWeight.bold,
                ),
              ),

              const SizedBox(
                height: 8,
              ),

              Text(
                'Informe os custos envolvidos '
                    'na comercialização.',
                style: TextStyle(
                  color:
                  Colors.grey.shade600,
                ),
              ),

              const SizedBox(
                height: 15,
              ),

              campo(
                'Frete',
                Icons.local_shipping,
                freteController,
              ),

              const SizedBox(
                height: 12,
              ),

              campo(
                'Armazenagem',
                Icons.warehouse,
                armazenagemController,
              ),

              const SizedBox(
                height: 12,
              ),

              campo(
                'Taxas',
                Icons.receipt_long,
                taxasController,
              ),

              const SizedBox(
                height: 20,
              ),

              // ==================================================
              // BOTÃO
              // ==================================================

              SizedBox(

                width:
                double.infinity,

                height: 55,

                child:
                ElevatedButton.icon(

                  onPressed: calcular,

                  icon: const Icon(
                    Icons.calculate,
                  ),

                  label: const Text(
                    'Calcular venda',
                    style: TextStyle(
                      fontSize: 16,
                      fontWeight:
                      FontWeight.bold,
                    ),
                  ),
                ),
              ),

              const SizedBox(
                height: 30,
              ),

              // ==================================================
              // RESULTADO
              // ==================================================

              Card(

                elevation: 2,

                shape:
                RoundedRectangleBorder(
                  borderRadius:
                  BorderRadius.circular(24),
                ),

                child: Padding(

                  padding:
                  const EdgeInsets.all(22),

                  child: Column(

                    crossAxisAlignment:
                    CrossAxisAlignment.start,

                    children: [

                      const Text(
                        '📊 Resultado da análise',
                        style: TextStyle(
                          fontSize: 20,
                          fontWeight:
                          FontWeight.bold,
                        ),
                      ),

                      const SizedBox(
                        height: 25,
                      ),

                      // ------------------------------------------
                      // PREÇO
                      // ------------------------------------------

                      linhaResultado(
                        'Preço de venda',
                        precoVenda,
                      ),

                      const SizedBox(
                        height: 15,
                      ),

                      // ------------------------------------------
                      // LOGÍSTICA
                      // ------------------------------------------

                      linhaResultado(
                        'Custos logísticos',
                        custoLogistica,
                      ),

                      const SizedBox(
                        height: 20,
                      ),

                      const Divider(),

                      const SizedBox(
                        height: 20,
                      ),

                      // ------------------------------------------
                      // PRODUTOR
                      // ------------------------------------------

                      const Text(
                        'Você recebe',
                        style: TextStyle(
                          fontSize: 15,
                          color:
                          Colors.grey,
                        ),
                      ),

                      const SizedBox(
                        height: 5,
                      ),

                      Text(
                        'R\$ ${valorProdutor.toStringAsFixed(2)}',
                        style: const TextStyle(
                          fontSize: 32,
                          fontWeight:
                          FontWeight.bold,
                        ),
                      ),

                      const SizedBox(
                        height: 25,
                      ),

                      // ------------------------------------------
                      // PERCENTUAL
                      // ------------------------------------------

                      Row(

                        mainAxisAlignment:
                        MainAxisAlignment.spaceBetween,

                        children: [

                          const Text(
                            'Impacto da logística',
                            style: TextStyle(
                              fontWeight:
                              FontWeight.w600,
                            ),
                          ),

                          Text(
                            '${percentualLogistica.toStringAsFixed(1)}%',
                            style:
                            const TextStyle(
                              fontWeight:
                              FontWeight.bold,
                            ),
                          ),
                        ],
                      ),

                      const SizedBox(
                        height: 10,
                      ),

                      // ------------------------------------------
                      // BARRA
                      // ------------------------------------------

                      LinearProgressIndicator(

                        value:
                        (percentualLogistica / 100)
                            .clamp(0.0, 1.0),

                        minHeight: 10,

                        borderRadius:
                        BorderRadius.circular(10),
                      ),

                      const SizedBox(
                        height: 15,
                      ),

                      // ------------------------------------------
                      // ANÁLISE
                      // ------------------------------------------

                      Container(

                        width:
                        double.infinity,

                        padding:
                        const EdgeInsets.all(15),

                        decoration:
                        BoxDecoration(
                          color:
                          Colors.grey.shade100,

                          borderRadius:
                          BorderRadius.circular(15),
                        ),

                        child: Row(

                          crossAxisAlignment:
                          CrossAxisAlignment.start,

                          children: [

                            const Text(
                              '💡',
                              style: TextStyle(
                                fontSize: 22,
                              ),
                            ),

                            const SizedBox(
                              width: 10,
                            ),

                            Expanded(

                              child: Text(
                                mensagemAnalise,
                                style:
                                const TextStyle(
                                  fontSize: 14,
                                ),
                              ),
                            ),
                          ],
                        ),
                      ),
                    ],
                  ),
                ),
              ),

              const SizedBox(
                height: 30,
              ),
            ],
          ),
        ),
      ),
    );
  }

  // ============================================================
  // WIDGET PARA LINHAS DO RESULTADO
  // ============================================================

  Widget linhaResultado(
      String titulo,
      double valor,
      ) {

    return Row(

      mainAxisAlignment:
      MainAxisAlignment.spaceBetween,

      children: [

        Text(
          titulo,
          style: const TextStyle(
            color: Colors.grey,
          ),
        ),

        Text(
          'R\$ ${valor.toStringAsFixed(2)}',
          style: const TextStyle(
            fontWeight:
            FontWeight.bold,
            fontSize: 16,
          ),
        ),
      ],
    );
  }

  // ============================================================
  // DESCARTAR CONTROLLERS
  // ============================================================

  @override
  void dispose() {

    precoController.dispose();
    freteController.dispose();
    armazenagemController.dispose();
    taxasController.dispose();

    super.dispose();
  }
}


```



``
