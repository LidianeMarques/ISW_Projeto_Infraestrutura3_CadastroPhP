# <h1 align="center"> Infraestrutura para Sistemas Web <h1>

## <h2 align="center">Projeto em Infraestrutura 3 - Cadastro simples em PhP <h2>
 <hr/>
  <div align="justify">
  
  <p>Esse projeto consiste em fazer um formulário simples de cadastro em php e salvar dados no banco de dados MySQLi. </p>
  <p>Requisitos:</p>  
  
  1. Criar um arquivo chamado cadatro.php;
  2. Criar um arquivo chamado conexao.php para conectar o PHP ao MySQLi;
  3. Criar um arquivo processa_cad_usuario.php responsável por salvar os dados do formulário no banco de dados.
 <hr/>
 
 ### 1. Criar um arquivo chamado <b> cadatro.php</b>. <h3>
  <p>O primeiro passo é montar o formulário com HTML5, criando o arquivo "cadatro.php", se prefirir copie e cole o código abaixo.</p>
  
   ~~~shell
<!DOCTYPE html>

<html>
    <head>
        <title> Cadastro</title>
    </head>
    </body>
        <form method="POST" action="processa_cad_usuario.php">
            Nome: <input type="text" name="txt_nome_usuario" placeholder="Digite o nome completo"><br><br>
            Telefone: <input type="text" name="txt_telefone_usuario" placeholder="Digite o seu telefone"><br><br>
            <input type="submit" value="Cadastrar">
        </form>
    </body>
</html>
 ~~~
 
 
  ### 2. Criar um arquivo chamado <b>conexao.php</b> para conectar o PHP ao MySQLi. <h3>
  <p> Depois de criar o formulário de cadastro, agora precisamos criar uma conexão com o banco.</p>
  <p>Obs. Em $usuario e  $senha coloque o usuário e senha do seu php admin.  </p>
 
  ~~~shell
<?php
    $servidor = "localhost";
    $usuario = "root";
    $senha = "";
    $dbname = "cadastro";
    
    //Criar a conexao
    $conn = mysqli_connect($servidor, $usuario, $senha, $dbname);
    
    if(!$conn){
        die("Falha na conexao: " . mysqli_connect_error());
    }else{
        //echo "Conexao realizada com sucesso";
    }  
?>
 ~~~
 
 ### 3. Criar um arquivo chamado <b>processa_cad_usuario.php</b>. <h3>
  <p> Depois de criar o formulário de cadastro e criar a conexão, agora precisamos salvar os dados do formulário no banco de dados.
Criando o arquivo <b>processa_cad_usuario.php</b>, se preferir, copie e colar o código abaixo.</p>
 
  ~~~shell
<?php
    include_once("conexao.php");
    $nome_usuario = $_POST['txt_nome_usuario'];
    $telefone_usuario = $_POST['txt_telefone_usuario'];
    //echo "$nome_usuario - $telefone_usuario";
    
    $result_usuario = "INSERT INTO usuarios(nome, telefone) VALUES ('$nome_usuario','$telefone_usuario')";
    $resultado_usuario = mysqli_query($conn, $result_usuario);
    
    if(mysqli_affected_rows($conn) == 1){
                echo "
                    <META HTTP-EQUIV=REFRESH CONTENT = '0;URL=http://localhost/aula/cadastro.php'>
                    <script type="text/javascript">
                        alert("Usuario cadastrado com Sucesso.");
                    </script>
                ";    
            }else{
                echo "
                    <META HTTP-EQUIV=REFRESH CONTENT = '0;URL=http://localhost/aula/cadastro.php'>
                    <script type="text/javascript">
                        alert("O Usuario não foi cadastrado com Sucesso.");
                    </script>
                ";    
            }
     mysqli_close($conn);
?>
 ~~~
 
 ### 3. Agora basta testar a aplicação. <h3>
  <p>Digite a url seguida do nome do formulário em php, igual ao exemplo abaixo:</p>
  
   ~~~url
    http://endereço_ip/cadastro.php
 ~~~
 
  <hr/>

<br/>

## Referências

[Como montar cadastro com PHP e MySQLi](https://celke.com.br/artigo/como-montar-cadastro-comphp-e-mysqli)
  
</div>
 
