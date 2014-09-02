HDT #6
=========
Asignador
=========

//****************************************************************
// Autores: Otto Wantland Carne: 13663 Diego Rodriguez Carne: 13111
// Seccion: 20
//Fecha 28/8/14
// Nombre de Archivo: Asignadora.java
// Breve Descripcion: contiene las funciones del asignador que permite guardar
// los datos esperados en el set
//*****************************************************************
import java.util.*;

public class Asignador
{
	//Atributos
	SetFactory<String> sFactory = new SetFactory<String>();
	private String opcion1, opcion2, opcion3, opcion4, nombre;
	private boolean continuar, subconjunto;
	private int contador, size, size2, size3, size4, size5;
	private String lista[], triple[], javaNotWeb[], webCelnotJava[], weborCel[];
	private Set<String> DesarolladoresJava, DesarolladoresWeb, DesarolladoresCel;
	
	//Constructor
	public Asignador (String opcion1, int tamanio)
	{
		DesarolladoresJava = sFactory.getSet(opcion1);
		DesarolladoresWeb = sFactory.getSet(opcion1);
		DesarolladoresCel = sFactory.getSet(opcion1);
		continuar = true;
		lista = new String[tamanio];
		size = tamanio;
		size2 = tamanio;
		size3 = tamanio;
		size4 = tamanio;
		size5 = tamanio;
		contador = 0;
	}
	
	//Metodo encargado de quitar los valores null de las listas creadas
	public void clearNull(String[] lista)
	{
		int taman = lista.length - 1;
		while (taman > -1)
		{
			String comparador = lista[taman];
			if (comparador == null)
			{
				lista[taman] = "";
				taman--;
			}
			else
			{
				taman--;
			}
		}
	}
	
	//Permite agregar un nuevo nombre a la lista de nombre usada por las funciones
	public void agregarNombre(String nombre)
	{
		lista[contador] = nombre;
		contador++;
	}
	
	//Permite volver la lista de nombres un String
	public String toString()
	{
		String resultado = "";
		for (String elemento:lista)
			resultado+= elemento;
		return resultado;
	}
	//Permite volver la lista triple un String
	public String tripleString()
	{
		String resultado = "";
		for (String elemento:triple)
			resultado = resultado + " 	" + elemento;
		return resultado;
	}
	//Permite volver la lista javaNotWeb un String
	public String notWeb()
	{
		String resultado = "";
		for (String elemento:javaNotWeb)
			resultado = resultado + " " + elemento;
		return resultado;
	}
	
	//Permite volver la lista webCelnotJava un String
	public String celWebntJava()
	{
		String resultado = "";
		for (String elemento:webCelnotJava)
			resultado+= " " + elemento;
		return resultado;
	}
	
	//Permite volver la lista weborCel un String
	public String webNtJava()
	{
		String resultado = "";
		for (String elemento:weborCel)
			resultado+= " " + elemento;
		return resultado;
	}
	
	//Imprime la respuesta a la pregunta sobre el subconjunto
	public String subconjuntoJavaWeb()
	{
		String resultado = " ";
		if (subconjunto == true)
		{
			resultado = "Si";
		}
		else
		{
			resultado = "No";
		}
		return resultado;
	}
	
	//Crea una lista de los desarolladores de Web o de Celular pero no de Java
	public void webOrCelNtJava()
	{
		weborCel = new String[size5];
		int counter2 = 0;
		int counter = size5 - 1;
		while (counter > -1)
		{
			boolean verdad = DesarolladoresJava.contains(lista[counter]);
			if (verdad == false)
			{
				boolean verdad2 = DesarolladoresWeb.contains(lista[counter]);
				boolean verdad3 = DesarolladoresCel.contains(lista[counter]);
				if (verdad2 == true || verdad3 == true)
				{
					weborCel[counter2] = lista[counter];
					counter2++;
					counter--;
				}
				else
				{
					counter--;
				}
			}
			else
			{
				counter--;
			}
		}
		clearNull(weborCel);
	}
	
	//Analiza si los desarolladores de Java son un subconjunto de los desarolladores Web
	public void javaSubconjunto()
	{
		int counter2 = 0;
		int counter = size5 - 1;
		while (counter > -1)
		{
			String nombre = lista[counter];
			boolean verdad = DesarolladoresJava.contains(nombre);
			if (verdad == true)
			{
				boolean verdad2 = DesarolladoresWeb.contains(nombre);
				if (verdad2 == true)
				{
					counter--;
					subconjunto = true;
				}
				else
				{
					subconjunto = false;
					break;
				}
			}
			else
			{
				counter--;
			}
		}

	}
	
	//Crea una lista con los desrolladores de las tres cosas a la vez
	public void TripleInterseccion()
	{
		triple = new String[size2];
		int counter2 = 0;
		int counter = size2 - 1;
		while (counter > -1)
		{
			boolean verdad = DesarolladoresWeb.contains(lista[counter]);
			if (verdad == true)
			{
				boolean verdad2 = DesarolladoresJava.contains(lista[counter]);
				if (verdad2 == true)
				{
					boolean verdad3 = DesarolladoresCel.contains(lista[counter]);
					if (verdad3 == true)
					{
						triple[counter2] = lista[counter];
						counter2++;
						counter--;
					}
					else
					{
						counter--;
					}
				}
				else
				{
					counter--;
				}
			}
			else
			{
				counter--;
			}
		}
		clearNull(triple);
	}
	
	//Crea una lista de los desarolladores de java pero no de Web
	public void javaNotWeb()
	{
		javaNotWeb = new String[size3];
		int counter2 = 0;
		int counter = size3 - 1;
		while (counter > -1)
		{
			boolean verdad = DesarolladoresWeb.contains(lista[counter]);
			if (verdad == false)
			{
				boolean verdad2 = DesarolladoresJava.contains(lista[counter]);
				if (verdad2 == true)
				{
					javaNotWeb[counter2] = lista[counter];
					counter2++;
					counter--;
				}
				else
				{
					counter--;
				}
			}
			else
			{
				counter--;
			}
		}
		clearNull(javaNotWeb);
	}
	
	//Crea una lista de los desarolladores de web y celular pero no Java
	public void webCellnotjava()
	{
		webCelnotJava = new String[size4];
		int counter2 = 0;
		int counter = size4 - 1;
		while (counter > -1)
		{
			boolean verdad = DesarolladoresWeb.contains(lista[counter]);
			if (verdad == true)
			{
				boolean verdad2 = DesarolladoresJava.contains(lista[counter]);
				if (verdad2 == false)
				{
					boolean verdad3 = DesarolladoresCel.contains(lista[counter]);
					if (verdad3 == true)
					{
						webCelnotJava[counter2] = lista[counter];
						counter2++;
						counter--;
					}
					else
					{
						counter--;
					}
				}
				else
				{
					counter--;
				}
			}
			else
			{
				counter--;
			}
		}
		clearNull(webCelnotJava);
	}
	
	//Se encarga de instanciar los datos sobre los desarolladores
	public void asignar()
	{
		//Pre: Obtiene la opcion del factory y decide en que lista guardar los datos
		//Post: Guarda los datos en el set deseado
		while (continuar == true)
		{
			Scanner input = new Scanner (System.in);
			System.out.println("Cual es el nombre de la persona? \n");
            nombre = input.next();
            input.nextLine();
            
            agregarNombre(nombre);
            
            System.out.println("Es desarollador de Java? \n");
            opcion2 = input.next();
            input.nextLine();
            if(opcion2.equals("si") || opcion2.equals("Si"))
            {
            	DesarolladoresJava.add(nombre);
            }
            
            System.out.println("Es desarollador de Web? \n");
            opcion3 = input.next();
            input.nextLine();
            if(opcion3.equals("si") || opcion3.equals("Si"))
            {
            	DesarolladoresWeb.add(nombre);
            }
            
            System.out.println("Es desarollador Celular? \n");
            opcion4 = input.next();
            input.nextLine();
            if(opcion4.equals("si")|| opcion4.equals("Si"))
            {
            	DesarolladoresCel.add(nombre);
            }
            
            if (size == 1)
            {
            	continuar = false;
            }
            else
            {
            	size = size -1;
            	continuar = true;
            }
		}
		//Permite ver que valores hay en cada Set
		System.out.println("Desarolladores de Java" + DesarolladoresJava);
		System.out.println("Desarolladores de Web" + DesarolladoresWeb);
		System.out.println("Desarolladores de Celular" + DesarolladoresCel);
	}
}


===========
SetFactory
==========

//****************************************************************
// Autores: Otto Wantland Carne: 13663 Diego Rodriguez Carne: 13111
// Seccion: 20
//Fecha 28/8/14
// Nombre de Archivo: SetFactory.java
// Breve Descripcion: ayuda a la eleccion de cualquier elemento del factory para
//utilizar en la toma de datos
//*****************************************************************
import java.util.*; //Utiliza JCF para llamar a los Sets

//Factory que se ocupa de decidir que tipo de set utilizar
class SetFactory <E>
{
	public Set<E> getSet(String entry)
	{
		if (entry.equals("1"))
		{
			return new HashSet<E>(); //Regresq un set de tipo HASH
		}
		else if (entry.equals("2")) //Regresa un set de tipo Tree
		{
			return new TreeSet<E>();
		}
		else
		{
			return new LinkedHashSet<E>(); //Regresa un set de tipo LinkedHash
		}
	}
}

====================
DriverAsignador.java
====================

//****************************************************************
// Autores: Otto Wantland Carne: 13663 Diego Rodriguez Carne: 13111
// Seccion: 20
//Fecha 28/8/14
// Nombre de Archivo: DriverAsignador.java
// Breve Descripcion: programa principal que trabaja con el asignador.
//*****************************************************************
import java.util.Scanner;
public class DriverAsignador
{
	public static void main(String[] args)
	{
		//Obtiene los datos necesarios para las operaciones como el 
		//numero de personas a ingresar
		Scanner input = new Scanner (System.in);
		System.out.println("Cuantas personas desea ingresar \n");
		String decision1 = input.next();
		int tamanio = Integer.parseInt(decision1);
		System.out.println("Que tipo de Set desea usar? \n"); //instancia el tipo de set que se desea usar
		System.out.println("1. Hash \n");
		System.out.println("2. Tree \n");
		System.out.println("3.LinkedHash \n");
		String decision = input.next();
		
		//Area que se encarga de utilizar los metodos e imprimir los datos esperados
		Asignador Asignador = new Asignador(decision, tamanio);
		Asignador.asignar();
		Asignador.TripleInterseccion();
		String listatxt = Asignador.tripleString();
		System.out.println("Desarolladores de los tres tipos " + listatxt);
		Asignador.javaNotWeb();
		String listatxt2 = Asignador.notWeb();
		System.out.println("Desarolladores de Java pero no de Web " + listatxt2);
		Asignador.webCellnotjava();
		String listatxt3 = Asignador.celWebntJava();
		System.out.println("Desarolladores de web y celulares pero no de Java " + listatxt3);
		Asignador.webOrCelNtJava();
		String listatxt4 = Asignador.webNtJava();
		System.out.println("Desarolladores de Web o celulares pero no de Java " + listatxt4);
		Asignador.javaSubconjunto();
		String listatxt5 = Asignador.subconjuntoJavaWeb();
		System.out.println("Desarolladores de Java son un subconjunto de Web" + listatxt5);
	}
}
