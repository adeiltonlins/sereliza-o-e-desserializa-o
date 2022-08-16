# sereliza-o-e-desserializa-o
///<summary>
/// Classe que identifica um Cliente
///</summary>

[Serializable()]public class Pedido

{
private int _id;
private DateTime _data;
[NonSerialized]private string _obs;
private Cliente _cliente;

///<summary>
/// Método construtor da Classe Pedido
///</summary>
///<param name="id">id do pedido</param>
///<param name="data">data do pedido</param>
///<param name="obs">observações gerais do pedido</param>
///<param name="cli">Cliente do pedido</param>
public Pedido(int id, DateTime data, string obs, Cliente cli)
{
_id = id;
_data = data;
_obs = obs;
_cliente = cli;
}

///<summary>
/// Property que retorna o ID do Pedido
///</summary>
public int id { get{return _id;} }

///<summary>
/// Property que retorna a data do Pedido
///</summary>
public DateTime data { get{return _data;} }

///<summary>
/// Property que retorna uma observaçao do Pedido
///</summary>
public string obs { get{return _obs;} }

///<summary>
/// Property que retorna o Cliente (o objeto inteiro será serializado)
///</summary>
public Cliente cliente { get{return _cliente;} }

}


desserialização
using System.Runtime.Serialization;
using System.Runtime.Serialization.Formatters.Soap;
using System.IO;

//definindo o formato e criando uma instância da classe SoapFormatter
IFormatter formato = new SoapFormatter();

//definindo o Stream de onde será lido o arquivo .xml
Stream file = new FileStream("Pedido.xml",
FileMode.Open ,FileAccess.Read , FileShare.Read );

//criando uma variável do tipo Pedido (vazia)
Pedido ped;

//agora sim, vamos desserializar o objeto
ped = (Pedido)formato.Deserialize(file);

//Stream fechado
file.Close();



