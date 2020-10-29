# Lógica Reconfigurável

## Projeto final - LCD Hardware

### Alunos:

 - Matheus Bigarelli
 - Victor Belinello


### Considerações iniciais

O controlador de LCD em VHDL foi baseado no código encontrado [aqui](https://www.digikey.com/eewiki/pages/viewpage.action?pageId=4096079).

Os arquivos presente nesse repositório são apenas os criados pela equipe, sem qualquer arquivo de projeto, executável, objeto, etc gerado pelas ferramentas utilizadas.


### Passo a passo para criação de projeto e execução de código

1. Colocar os arquivos no diretório desejado.

2. Criar projeto no Quartus II 13.0 SP1<br/>
    2.1 Se quiser nomear o projeto como nios_system, este é o nome do sistema no Qsys.<br/>
    2.2 Senão, nomeie o projeto como quiser e coloque o sistema nios_system como componente TopLevel.<br/>
    2.3 Adicione os arquivos .vhd deste repositório ao projeto.<br/>
    2.4 Escolha a placa: Família Cyclone 2; EP2C35F672C6.

3. Abrir Qsys<br/>
    3.1 Abrir sistema nios_system.qsys<br/>
    3.2 Certifique-se de que os conduítes do componente lcd_avalon_interface estão exportados corretamente e todas as conexões foram feitas.<br/>
    3.3 Na aba generate, selecione a síntese com VHDL<br/>
    3.4 Foi deixado marcado para criar os Block Symbol Files, mas não se sabe até o momento da criação deste README se é necessário.<br/>
    3.5 Gere os arquivos de síntese

4. Execute a Análise e Síntese de projeto.

5. Abra o Pin Planner e faça as seguintes conexões (se for a mesma placa - EP2C35F672C6)
    |       Sinal               |  Pino      |
    | ------------------------- | ---------- |
    | clk_clk                   | N2         |
    | en_export_export          | K3         |
    | lcd_data_export_export[7] | H3         |
    | lcd_data_export_export[6] | H3         |
    | lcd_data_export_export[5] | H3         |
    | lcd_data_export_export[4] | H3         |
    | lcd_data_export_export[3] | H3         |
    | lcd_data_export_export[2] | H3         |
    | lcd_data_export_export[1] | H3         |
    | lcd_data_export_export[0] | H3         |
    | reset_n_reset_n           | G26 (Key0) |
    | rs_export_export          | K1         |
    | rw_export_export          | K4         |
    | lcd_blon_export_export    | K2         |
    | lcd_on_export_export      | L4         |

6. Compile o projeto.

7. Abrir programmer e fazer download na placa.

8. Abrir NIOS II SBT for Eclipse.<br/>
    8.1 Criar pasta software dentro do diretório do projeto.

9. Criar projetos<br/>
    9.1 Criar novo projeto com BSP.<br/>
    9.2 Selecionar o sopcinfo gerado.

10. Incluir códigos .c e .h no projeto criado no eclipse.

11. No projeto do BSP, clicar com botão direito > Nios 2 > Generate BSP

12. Build BSP

13. Build projeto de software.

14. Executar programa<br/>
    14.1 Clicar com botão direito no projeto de software.<br/>
    14.2 Run As > Run configurations...<br/>
    14.3 Clicar duas vezes em Nios 2 Hardware.<br/>
    14.4 Verificar o projeto foi está listado corretamente na aba Project<br/>
    14.5 Na aba Target Connection, clicar em Refresh Connections.<br/>
    14.6 Clicar em Run

15. Reze.
