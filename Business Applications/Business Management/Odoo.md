?debug=assets
$.... --dev=all
### XML Files
* Starting Template
      <?xml version="1.0" encoding="UTF-8"?>
      <odoo>
        <!-- Your code goes here -->
      </odoo>


## Modules
### Building a Module (summarized steps)
1. Make Starting code:
       $ odoo-bin scaffold <module name> <where to put it>
2. Uncomment the code for (Python Models Classs) and XML views
3. Run the Odoo Server:
       $ python --dev=all -c /path/to/my/oodo/config/file
4. Update apps list: top menu -> Apps -> Update Apps List

### Structure of a Module
* Business objects
 * Models (Python classes)
* Object views
 * Definition of business objects UI display
* Data files
  * views or reports
  * configuration data (modules parametrization, security rules)
  * demonstration data
  * ...
* Web controllers
 * Handle requests from web browsers
* Static web data
 * Images, CSS or javascript

#### Models
* ##### Model Fields
 * ###### Field Types
* ##### Relations between models

### Views
#### Generic structure
>Placeholders are denoted in all caps

    <record id="MODEL_view_TYPE" model="ir.ui.view">
      <field name="name">NAME</field>
      <field name="model">MODEL</field>
      <field name="arch" type="xml">
        <VIEW_TYPE>
          <VIEW_SPECIFICATIONS/>
        </VIEW_TYPE>
      </field>
    </record>
* ##### Generic View Fields:
 * `name` (mandatory) Char
 * `model` Char
 * `arch` Text
 * `inherit_id`Many2one

###### `name` Field:
    <field name="name">NAME</field>
###### `model` Field:
    <field name="model">MODEL</field>
The model linked to the view, if applicable.
###### `arch` Field:
    <field name="arch" type="xml">
      ...
    </field>
The description of the view layout

  * `arch` Field Children:
   * `xpath`
           <xpath expr="page[@name='pg']/group[@name='gp']/field" position="inside">
            <field name="description"/>
          </xpath>
   * `field` element with a `name` attribute
          <field name="res_id" position="after"/>
   * any other element
          <div name="name" position="replace">
            <div name="name2">
              <field name="name2"/>
            </div>
          </div>

###### `inherit_id` Field:
    <field name="inherit_id" ref="crm.view_crm_case_opportunities_filter"/>
the current view’s parent view, unset by default


#### Actions & Menus
* Actions and menus are regular records in database
* Declared through data files (__usually__)
      <record model="ir.actions.act_window" id="action_list_ideas">
          <field name="name">Ideas</field>
          <field name="res_model">idea.idea</field>
          <field name="view_mode">tree,form</field>
      </record>
      <menuitem id="menu_ideas" parent="menu_root" name="Ideas" sequence="10"
                action="action_list_ideas"/>

##### Actions
* The _action_ must be declared before its corresponding _menu_ in the XML file
* Declare with a `<record model="ir.actions.act_window" ...>...</record>`

##### Menus
* Declare with a `<menuitem .../>` _shortcut_
      <menuitem id="menu_ideas" parent="menu_root" name="Ideas" sequence="10"
        action="action_list_ideas"/>
  * `parent="menu_root"`: the parent is root, so this is a root menu

#### Basic Views
* ##### Generic View
      <record model="ir.ui.view" ...>
        <field...></field>
        <field...></field>
        ...
        <field name="arch" type="xml">
            <!-- view content: <form>, <tree>, <graph>, ... -->
        </field>
      </record>

* ##### Tree/List View
      <tree string="Idea list">
        <field ..."/>
        <field .../>
      </tree>
* ##### Forms View
 * Their root element is `<form>`
 * They are composed of high-level structure elements (`groups`, `notebooks`) and interactive elements (`buttons` and `fields`)

        <form string="Idea form">
          <group colspan="4">
             <group colspan="2" col="2">
                 <separator string="General stuff" colspan="2"/>
                 <field name="name"/>
                 <field name="inventor_id"/>
             </group>

             <group colspan="2" col="2">
                 <separator string="Dates" colspan="2"/>
                 <field name="active"/>
                 <field name="invent_date" readonly="1"/>
             </group>

             <notebook colspan="4">
                 <page string="Description">
                     <field name="description" nolabel="1"/>
                 </page>
             </notebook>

             <field name="state"/>
          </group>
        </form>


* ##### Search View

##### Model Data
>Module data is declared via data files, XML files with `<record>` elements

>Each `<record>` element creates or updates a database record

* Syntax:
      <odoo>
          <record model="{model name}" id="{record identifier}">
              <field name="{a field name}">{a value}</field>
          </record>
      </odoo>

* Old syntax:??

      <openerp>
          <data>
              <record id="demo_multi_session" model="pos.multi_session">
                  <field name="name">multi session demo</field>
              </record>
          </data>
      openerp>


## QWeb
* QWeb is the primary templating engine used by Odoo2
* It is an **XML** templating engine and used mostly to generate HTML fragments and pages

### Template Directives
* `t-if` for Conditionals
      <t t-if="condition">
          <p>Test</p>
      </t>



## Tags
* ### `<filter>` tag
`<filter string="Lost" name="ep_lost" domain="['&amp;', ('active', '=', False), ('probability', '=', 0)]"/>`

 * `string`
  >the field’s label
 *
