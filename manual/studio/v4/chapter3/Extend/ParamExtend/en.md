#Properties Extension #

### Widget Types ###

Cocos Studio supports extensions of widgets and widgets’ properties. The editor has some general settings of widgets' properties in default. It is also recommended to add custom properties to widgets (For more information, see Sample). 

A series of widget types is available in Cocos Studio.

- **string type**    

   ![image](res_en/image001.png)

Frame event is a string type with a text field, which has no text format restriction and can also be blank. For example: 

    string customString = string.Empty;
    [UndoPropertyAttribute] 
    [DisplayName("字符串")]
    [Category("Custom_Plug")]
    [PropertyOrder(0)]
    [Browsable(true)]
    public string CustomString
    {
        get { return customString; }
        set
        {
            if (customString != value)
            {
                customString = value;
                this.RaisePropertyChanged(() => this.CustomString);
            }
        }
    }

![image](res_en/image002.png)

Name is a string type with a text field, which has no text format restriction but cannot be blank. If it is blank, it will restore the previous value by default. Such text field can be applied by calling **ValidTextEditor**. For example: 

    [UndoPropertyAttribute]
    [DisplayName("ValidTextBox")]
    [Editor(typeof(ValidTextEditor), typeof(ValidTextEditor))] 
    [Category("Custom_Plug")]
    [PropertyOrder(0)]
    [Browsable(true)]
    public string ValidTextBoxString { get; set; }

- **int type**

Logical Label is an **int** type with a text field only for numbers extending from -9999999 to 9999999, which can be set by **SetMaxMin**. For example: 

    int customInt = 0;
    [UndoPropertyAttribute]
    [DisplayName("Integer")]
    [Category("Custom_Plug")]
    [PropertyOrder(1)]
    [Browsable(true)]
    public int CustomInt
    {
        get { return customInt; }
        set
        {
            if (customInt != value)
            {
                customInt = value;
                this.RaisePropertyChanged(() => this.CustomInt);
            }
        }
    }

- **bool type**

![image](res_en/image003.png)

Visible is a **bool** type with a check box, which can be checked or unchecked. For example：

    bool customBool = false;
    [UndoPropertyAttribute]
    [DisplayName("Bool")]
    [Category("Custom_Extend")]
    [PropertyOrder(4)]
    [Browsable(true)]
    public bool CustomBool
    {
        get { return customBool; }
        set
        {
            if (customBool != value)
            {
                customBool = value;
                this.RaisePropertyChanged(() => this.CustomBool);
            }
        }
    }

- **enum type**

![image](res_en/image004.png)

Alignment is an **enmu** type with a combox, in which various enmu items can be selected. For example: 

    public enum CocosEnum
    {
        None,
        Fir,
        Sec,
        Thi
    }

    CocosEnum customEnum = CocosEnum.None;

    [UndoPropertyAttribute]
    [DisplayName("Enum")]
    [Category("Custom_Plug")]
    [PropertyOrder(5)]
    [Browsable(true)]
    public CocosEnum CustomEnum
    {
        get { return customEnum; }
        set
        {
            if (customEnum != value)
            {
                customEnum = value;
                this.RaisePropertyChanged(() => this.CustomEnum);
            }
        }
    }

- **Color type**

![image](res_en/image005.png)

Color-blend is a Color type with a combined control, in which various color can be selected. For example: 

	System.Drawing.Color customColor = System.Drawing.Color.White;
	[UndoPropertyAttribute]
	[Editor(typeof(ColorEditor), typeof(ColorEditor))]
	[DisplayName("Color")]
	[Category("Custom_Extend")]
	[PropertyOrder(6)]
	[Browsable(true)]
	public System.Drawing.Color CustomColor
	{
	    get { return customColor; }
	    set
	    {
	        if (customColor != value)
	        {
	            customColor = value;
	            this.RaisePropertyChanged(() => this.CustomColor);
	        }
	    }
	}

- **ScaleValue type**

![image](res_en/image006.png)

Skew is a **ScaleValue** type with a combined control, in which the value of X and Y can be set separately. Minimum/ Maximum values and value range can be set in property. For example: 

	ScaleValue customScaleValue = new ScaleValue(1, 1);
	[UndoPropertyAttribute]
	[Editor(typeof(CustomEditor), typeof(CustomEditor))] 
	[ValueRange(int.MinValue, int.MaxValue, 1)]
	[DisplayName("ScaleValue")]
	[Category("Custom_Extend")]
	[PropertyOrder(7)]
	[Browsable(true)]
	public ScaleValue CustomScaleValue
	{
	    get { return customScaleValue; }
	    set
	    {
	        if (customScaleValue != value)
	        {
	            customScaleValue = value;
	            this.RaisePropertyChanged(() => this.CustomScaleValue);
	        }
	    }
    }

- **PointF type**

![image](res_en/image007.png)

The anchor attribute is a **PoinfF** Type. Type refers to a combined control, in which the value of X and Y can be set separately. For example:

	PointF customPointF = new PointF(1, 1);
	[UndoPropertyAttribute]
	[Editor(typeof(PointFEditor), typeof(PointFEditor))]
	[ValueRange(int.MinValue, int.MaxValue, 1)]
	[DisplayName("ScaleValue")]
	[Category("Custom_Extend")]
	[PropertyOrder(7)]
	[Browsable(true)]
	public PointF CustomPointF
	{
	    get { return customPointF; }
	    set
	    {
	        if (customPointF != value)
	        {
	            customPointF = value;
	            this.RaisePropertyChanged(() => this.CustomScaleValue);
	        }
	    }
	}


Some properties are available in the sample file of **CustomObject**. After adding these properties, users need to add the corresponding properties in **CustomObjectData** class, so that property settings can be saved when exit the editor. Previously saved property settings will be read when a file is opened. For example: 

        [ItemProperty]
        [JsonProperty]
        public int CustomInt { get; set; }

The specific codes have been added to **CustomObjectData**.

### **Creating a Custom Widget** ###

- **CustomEditor** inherits **BaseEditor** base class and **ITypeEditor** interface.

    **ITypeEditor** interface should implement **ResolveEditor**. With this method, a control will display on the canvas panel. To display more controls, users need to put them in a Container, such as a Table. After settings of the controls in Container, the Container will be displayed on the canvas. 

- **NumberEditorWidget** is a control with two **TextBox** (similar to controls of ScaleValue type).

    When setting two **TextBox** value, add the following two events: 

     `_widget.PointX += widget_PointX;`

     `_widget.PointY += widget_PointY;`

    **PointX** and **PointY** are two separate events for **TextBox**.

	private void widget_PointX(object sender, PointEvent e)
	{
		_scaleValue.ScaleX = (float)e.PointX;
		UpdatePropertyValue(_propertyItem.PropertyData, _scaleValue);
	}
- To create a custom widget, do the following: 

    1 Assign values to **scaleValue**: 	
	scaleValue.ScaleX = (float)e.PointX;

    2 Call **UpdatePropertyValue** to modify rendering section. Any change in the rendering section will trigger the event `override void OnPropertyChanged(object sender,PropertyChangedEventArgs e)`. 

    3 Add logical codes in OnPropertyChanged if changes are needed. (Source Codes are in **CustomEditor** file.)

***Note** The contents of the document are under continuous update based on users' feedback. Please check the latest version for reference. If you have any suggestions or comments on the extensions of Cocos Studio, please let us know. Thanks for your interest and support for Cocos Studio, and for helping us make a better product.*  