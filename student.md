# sanbeijiu
new
**********.h***********************
#ifndef XSGL_H
#define XSGL_H


#include<QDateEdit>

#include<QtGui>
class	BasicLayout:public QDialog
 {
                              Q_OBJECT

 public:
     BasicLayout(QWidget *parent=0,Qt::WFlags flags=0);
    ~BasicLayout();

 private:
    QTextCodec *code;
    QTabWidget *tabWgt;
     QTableWidget *stuTableWgt;
    QWidget *pageTab[20];
    QLabel *numLb;
    QLineEdit *numEt;
    QLineEdit *nameEt;

          QLabel	*id;
          QLabel	*name;
          QLabel	*sex;

          QLabel	*min;
          QLabel	*age;
          QLabel	*date;

          QLineEdit	*ide;
          QLineEdit	*namee;
          QDateEdit *de;
         QRadioButton *rb[2];


           QCheckBox                              *y[3];
          QComboBox                             *   combo;
         QSpinBox                            *        ag;
        QLabel                             *           labHead;
       QLabel                            *             labIndividual;
       PushButton                       *              btnChange;
       TextEdit                        *               edtIndividual;
       QTextEdit	                                    *edi;
        QPushButton	                                 *dl;
         QPushButton	                              *ad;
          QPushButton	                            *btnopen;
            QPushButton	                        *add;
              QPushButton	                    *change;
                QPushButton	                 *del;
                  QPushButton	             *sure;
                    QPushButton	         *find;
                      QPushButton	     *btnquit;
                        QPushButton*btnsave;
 };


#endif // XSGL_H
***************************main****************************************
#include "xsgl.h"
#include<QApplication>
int main(int argc,char **argv){
     QApplication app(argc,argv);
    BasicLayout*w=new BasicLayout;
    w->setGeometry(400,400,1000,500);
     w->setAutoFillBackground(true);
     QPixmap pmap("/home/21.png");
     QBrush brush(pmap.scaled(w->size()));
     QPalette pal=w->palette();
     pal.setBrush(QPalette::Window,brush);
     w->setPalette(pal);
     w->show();
     return app.exec();
   }
****.*********************.cppp********************************
   
   #include "xsgl.h"

BasicLayout::BasicLayout(QWidget*parent,Qt::WFlags flags):QDialog(parent,flags){
    code=QTextCodec::codecForLocale();
    setWindowTitle(code->toUnicode("学生信息系统"));
    QGridLayout*leftLayou=new QGridLayout;
    tabWgt=new QTabWidget(this);
    leftLayou->addWidget(tabWgt,0,1);
    char *pageName[3]={"基本信息","学校信息","社会经历"};
    int i;
    for(i=0;i<3;i++){
        pageTab[i]=new QWidget(this);
        tabWgt->addTab(pageTab[i],code->toUnicode(pageName[i]));
    }

    //page0
    
        QGridLayout*dat=new QGridLayout;
        id =new QLabel(code->toUnicode("学号"),pageTab[0]);
        name =new QLabel(code->toUnicode("姓名"),pageTab[0]);
        sex =new QLabel(code->toUnicode("性别"),pageTab[0]);
        min =new QLabel(code->toUnicode("民族"),pageTab[0]);
        age =new QLabel(code->toUnicode("年龄"),pageTab[0]);
        date =new QLabel(code->toUnicode("出生日期"),pageTab[0]);

        ide=new QLineEdit(pageTab[0]);
        namee=new QLineEdit(pageTab[0]);
        de=new QDateEdit(pageTab[0]);
        rb[0]=new QRadioButton(code->toUnicode("男"));
        rb[1]=new QRadioButton(code->toUnicode("女"));
          ag= new QSpinBox (pageTab[0]);

          combo = new QComboBox(this);
          combo->setEditable(true);
          combo->insertItem(0, QIcon( "1" ),code->toUnicode("汉"));
          combo->insertItem(1, QIcon( "2" ),code->toUnicode("蒙"));
          combo->insertItem(2, QIcon( "3" ),code->toUnicode("壮"));
          combo->insertItem(3, QIcon( "4" ),code->toUnicode("回"));

          dat->addWidget(id,0,0);
          dat->addWidget(ide,0,1,1,2);
          dat->addWidget(name,0,3,1,1);
          dat->addWidget(namee,0,4,1,1);

          dat->addWidget(sex,1,0);
          dat->addWidget(rb[0],1,1,1,1);
          dat->addWidget(rb[1],1,2,1,1);
          dat->addWidget(min,1,3,1,1);
          dat->addWidget(combo,1,4,1,2);

          dat->addWidget(age,2,0);
          dat->addWidget(ag,2,1,1,2);
          dat->addWidget(date,2,3,1,1);
          dat->addWidget(de,2,4,1,1);

              pageTab[0]->setLayout(dat);
//page1

               QGridLayout*bat=new QGridLayout;
               id =new QLabel(code->toUnicode("学校"),pageTab[1]);
               bat->addWidget(id,0,0);
               ide=new QLineEdit(pageTab[1]);
               bat->addWidget(ide,0,1,1,3);

               name =new QLabel(code->toUnicode("专业"),pageTab[1]);
               bat->addWidget(name,1,0);
               ide=new QLineEdit(pageTab[1]);
               bat->addWidget(ide,1,1,1,3);

               sex =new QLabel(code->toUnicode("入学日期"),pageTab[1]);
               bat->addWidget(sex,2,0);
               de=new QDateEdit(pageTab[1]);
               bat->addWidget(de,2,1,1,2);

               min =new QLabel(code->toUnicode("语言"),pageTab[1]);
               bat->addWidget(min,3,0);
               y[0]=new QCheckBox(code->toUnicode("英语"),pageTab[1]);
               bat->addWidget(y[0],3,1);
               y[1]=new QCheckBox(code->toUnicode("俄语"),pageTab[1]);
               bat->addWidget(y[1],3,2);
               y[2]=new QCheckBox(code->toUnicode("法语"),pageTab[1]);
               bat->addWidget(y[2],3,3);
                   pageTab[1]->setLayout(bat);

//page2

             QGridLayout*at=new QGridLayout;
             edi=new QTextEdit;
             at->addWidget(edi,0,0,1,4);
             ide=new QLineEdit(pageTab[2]);
             ad=new QPushButton(code->toUnicode("添加"));
             dl=new QPushButton(code->toUnicode("删除"));
             at->addWidget(ad,1,2);
             at->addWidget(dl,1,3);
             at->addWidget(ide,1,0,1,2);
                 pageTab[2]->setLayout(at);
                 

//Right 自 and testedit
                               labHead	=new QLabel(code->toUnicode("自我评价"));
                               QHBoxLayout*headLayout=new QHBoxLayout;
                               headLayout->addWidget(labHead);
                               headLayout->setSpacing(10);
                               edtIndividual=new QTextEdit;
                               QVBoxLayout*rightLayout=new QVBoxLayout;
                               rightLayout->addLayout(headLayout);
                               rightLayout->addWidget(edtIndividual);
                               rightLayout->setMargin(10);
//添加

                               add=new QPushButton(code->toUnicode("添加"));
                               del=new QPushButton(code->toUnicode("删除"));
                               change=new QPushButton(code->toUnicode("修改"));
                               sure=new QPushButton(code->toUnicode("确定"));
                               find=new QPushButton(code->toUnicode("查找"));
                               btnsave=new QPushButton(code->toUnicode("保存文件"));
                               btnopen=new QPushButton(code->toUnicode("打开文件"));
                               btnquit=new QPushButton(code->toUnicode("退出"));

                         QHBoxLayout*bottomLayout1=new QHBoxLayout;
                              // bottomLayout1->addStretch();
                               bottomLayout1->addWidget(add);
                               bottomLayout1->addWidget(change);
                               bottomLayout1->addWidget(sure);
                               bottomLayout1->addWidget(del);
                               bottomLayout1->addWidget(find);
                               bottomLayout1->setSpacing(5);
                         QHBoxLayout*bottomLayout=new QHBoxLayout;
                               bottomLayout->addWidget(btnsave);
                               bottomLayout->addWidget(btnopen);
                               bottomLayout->addWidget(btnquit);
                               bottomLayout->setSpacing(4);

//tab

                              QGridLayout*tab=new QGridLayout;
                              stuTableWgt =new QTableWidget(this);
                              tab-> addWidget(stuTableWgt,2,0);

                               stuTableWgt->setRowCount(15);
                               stuTableWgt->setGeometry(10,80,960,480);
                               stuTableWgt->setColumnCount(9);//设置列数
                               char *headName[]={"学号","姓名","性别","年龄","民族","出生日期","所在学校","专业","入学日期"};
                               int  headWidth[]={80,80,50,50,70,100,180,120,100};
                               QStringList headList;
                               qDebug("init");
                               int a;
                               for(a=0;a<9;a++) headList.append(code->toUnicode(headName[a]));
                               stuTableWgt->setHorizontalHeaderLabels(QStringList(headList));
                               for(a=0;a<9;a++)  stuTableWgt->setColumnWidth(i,headWidth[a]);
//mai
                         QGridLayout*mainLayout=new QGridLayout(this);
                             mainLayout->addLayout(leftLayou,0,0);
                             mainLayout->addLayout(rightLayout,0,1);
                             mainLayout->addLayout(bottomLayout1,1,0);
                             mainLayout->addLayout(bottomLayout,1,1);
                             mainLayout->addLayout(tab,2,0,1,2);

                               mainLayout->setMargin(15);
                               mainLayout->setSpacing(20);
                               mainLayout->setSizeConstraint(QLayout::SetFixedSize);
  }

  BasicLayout::~BasicLayout()
  {
  }

