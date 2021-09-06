# UML (unified modelling language) 

Tool like draw.io offers the uml feature to prepair professional the thinkprocess for ode modelling.


The name of the class is in the upper third of the rectangle in UML notation. The attributes are in the middle third. Our example class StockItem defines the two attributes m_name and m_value, i.e. the name of the stock and the current market value. The minus sign in front of the attributes means that they are private members of the class, i.e. they cannot be accessed directly from outside.
In the lower third are the methods of the StockItem class. The plus sign in front of them shows that they are public, i.e. the methods may be called by other objects. This shows the principle of encapsulation: Instead of accessing the attribute m_value directly, other objects must use the access methods setValue() and getValue()! So the developer of the class has the possibility to include additional queries in setValue(), e.g. concerning the validity of the parameter.
