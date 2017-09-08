---
title: "カスタム レポート アイテムのデザイン時コンポーネントの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- custom report items, creating
ms.assetid: 323fd58a-a462-4c48-b188-77ebc0b4212e
caps.latest.revision: 37
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 0b1f5649db2f99957ad3b2452b02d2f7b2db01cb
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="creating-a-custom-report-item-design-time-component"></a>カスタム レポート アイテムのデザイン時コンポーネントの作成
  カスタム レポート アイテムのデザイン時コンポーネントは、Visual Studio レポート デザイナー環境で使用できるコントロールです。 カスタム レポート アイテムのデザイン時コンポーネントは、ドラッグ アンド ドロップ操作を使用できるアクティブ化されたデザイン画面、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロパティ ブラウザーとの統合、およびカスタム プロパティ エディター機能を提供します。  
  
 カスタム レポート アイテムのデザイン時コンポーネントを使用すると、ユーザーは、デザイン環境のレポート上にカスタム レポート アイテムを配置し、カスタム レポート アイテムのカスタム データ プロパティを設定してから、カスタム レポート アイテムをレポート プロジェクトの一部として保存できます。  
  
 開発環境でデザイン時コンポーネントを使用して設定されるプロパティは、ホスト デザイン環境によってシリアル化およびシリアル化解除され、レポート定義言語 (RDL) ファイルに要素として格納されます。 レポート プロセッサによるレポートの実行時には、デザイン時コンポーネントを使用して設定されたプロパティが、レポート プロセッサによってカスタム レポート アイテムの実行時コンポーネントに渡されます。実行時コンポーネントは、カスタム レポート アイテムを表示してレポート プロセッサに返します。  
  
> [!NOTE]  
>  カスタム レポート アイテムのデザイン時コンポーネントとして実装、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]コンポーネントです。 ここでは、カスタム レポート アイテムのデザイン時コンポーネントに固有の実装詳細について説明します。 使用してコンポーネントの開発の詳細については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]を参照してください[Visual Studio のコンポーネント](http://go.microsoft.com/fwlink/?LinkId=116576)MSDN ライブラリです。  
  
 完全に実装されたカスタム レポート アイテムのサンプルについては、次を参照してください。 [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="implementing-a-design-time-component"></a>デザイン時コンポーネントの実装  
 カスタム レポート アイテムのデザイン時コンポーネントのメイン クラスを継承、 **Microsoft.ReportDesigner.CustomReportItemDesigner**クラスです。 標準の属性の使用に加えて、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]コントロール、コンポーネント クラスを定義する必要があります、 **CustomReportItem**属性。 この属性は、reportserver.config ファイルに定義されたカスタム レポート アイテム名と同じにする必要があります。 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 属性の完全な一覧については、[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK ドキュメントの「属性」を参照してください。  
  
 次のコード例では、カスタム レポート アイテムのデザイン時コントロールに属性が適用されています。  
  
```csharp  
namespace PolygonsCRI  
{  
    [LocalizedName("Polygons")]  
    [Editor(typeof(CustomEditor), typeof(ComponentEditor))]  
        [ToolboxBitmap(typeof(PolygonsDesigner),"Polygons.ico")]  
        [CustomReportItem("Polygons")]  
  
    public class PolygonsDesigner : CustomReportItemDesigner  
    {  
...  
```  
  
### <a name="initializing-the-component"></a>コンポーネントの初期化  
 カスタム レポート アイテム用にユーザーが指定したプロパティは、<xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> クラスを使用して渡されます。 実装、 **CustomReportItemDesigner**クラスをオーバーライドする必要があります、 **InitializeNewComponent**コンポーネントの新しいインスタンスを作成するメソッド<xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>クラスし、既定値に設定します。  
  
 次のコード例は、カスタム レポート アイテムのデザイン時コンポーネント クラスをオーバーライドする例を示しています、 **CustomReportItemDesigner.InitializeNewComponent**コンポーネントの初期化するメソッドを<xref:Microsoft.ReportingServices.RdlObjectModel.CustomData>クラス。  
  
```csharp  
public override void InitializeNewComponent()  
        {  
            CustomData = new CustomData();  
            CustomData.DataRowHierarchy = new DataHierarchy();  
  
            // Shape grouping  
            CustomData.DataRowHierarchy.DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].Group.Name = Name + "_Shape";  
            CustomData.DataRowHierarchy.DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Point grouping  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers.Add(new DataMember());  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group = new Group();  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.Name = Name + "_Point";  
            CustomData.DataRowHierarchy.DataMembers[0].DataMembers[0].Group.GroupExpressions.Add(new ReportExpression());  
  
            // Static column  
            CustomData.DataColumnHierarchy = new DataHierarchy();  
            CustomData.DataColumnHierarchy.DataMembers.Add(new DataMember());  
  
            // Points  
            IList<IList<DataValue>> dataValues = new List<IList<DataValue>>();  
            CustomData.DataRows.Add(dataValues);  
            CustomData.DataRows[0].Add(new List<DataValue>());  
            CustomData.DataRows[0][0].Add(NewDataValue("X", ""));  
            CustomData.DataRows[0][0].Add(NewDataValue("Y", ""));  
        }  
```  
  
### <a name="modifying-component-properties"></a>コンポーネントのプロパティの変更  
 変更することができます**CustomData**いくつかの方法で、デザイン環境でのプロパティです。 デザイン時コンポーネントによって公開され、<xref:System.ComponentModel.BrowsableAttribute> 属性でマークされたあらゆるプロパティは、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] プロパティ ブラウザーを使用して変更できます。 または、デザイン環境でコントロールを右クリックして、カスタム レポート アイテムのデザイン サーフェイスに項目をドラッグして、プロパティを変更するさらに、**プロパティ**ショートカット メニューのカスタム プロパティ ウィンドウを表示します。  
  
 次のコード例は、 **Microsoft.ReportDesigner.CustomReportItemDesigner.CustomData**プロパティを持つ、<xref:System.ComponentModel.BrowsableAttribute>属性を適用。  
  
```csharp  
[Browsable(true), Category("Data")]  
public string DataSetName  
{  
      get  
      {  
         return CustomData.DataSetName;  
      }  
      set  
      {  
         CustomData.DataSetName = value;  
      }  
   }  
  
```  
  
 デザイン時コンポーネントに、カスタム プロパティ エディター ダイアログ ボックスを挿入できます。 カスタム プロパティ エディターの実装では、<xref:System.ComponentModel.ComponentEditor> クラスを継承し、プロパティ編集用ダイアログ ボックスのインスタンスを作成する必要があります。  
  
 次の例は、<xref:System.ComponentModel.ComponentEditor> を継承し、カスタム プロパティ エディター ダイアログ ボックスを表示するクラスの実装です。  
  
```csharp  
internal sealed class CustomEditor : ComponentEditor  
{  
   public override bool EditComponent(  
      ITypeDescriptorContext context, object component)  
    {  
     PolygonsDesigner designer = (PolygonsDesigner)component;  
     PolygonProperties dialog = new PolygonProperties();  
     dialog.m_designerComponent = designer;  
     DialogResult result = dialog.ShowDialog();  
     if (result == DialogResult.OK)  
     {  
        designer.Invalidate();  
        designer.ChangeService().OnComponentChanged(designer, null, null, null);  
        return true;  
     }  
     else  
        return false;  
    }  
}  
```  
  
 カスタム プロパティ エディター ダイアログ ボックスで、レポート デザイナーの式エディターを呼び出すことができます。 次の例では、コンボ ボックスの最初の要素をユーザーが選択すると、式エディターが呼び出されます。  
  
```csharp  
private void EditableCombo_SelectedIndexChanged(object sender,   
    EventArgs e)  
{  
   ComboBox combo = (ComboBox)sender;  
   if (combo.SelectedIndex == 0 && m_launchEditor)  
   {  
      m_launchEditor = false;  
      ExpressionEditor editor = new ExpressionEditor();  
      string newValue;  
      newValue = (string)editor.EditValue(null, m_designerComponent.Site, m_oldComboValue);  
      combo.Items[0] = newValue;  
   }  
}  
  
```  
  
### <a name="using-designer-verbs"></a>デザイナー動詞の使用  
 デザイナー動詞は、イベント ハンドラーにリンクされたメニュー コマンドです。 デザイナー動詞を追加して、カスタム レポート アイテムの実行時コントロールのデザイン環境での使用時に、コンポーネントのショートカット メニューに表示できます。 使用して、実行時コンポーネントから使用可能なデザイナー動詞の一覧を返すことができます、**動詞**プロパティです。  
  
 次のコード例では、デザイナー動詞とイベント ハンドラーが <xref:System.ComponentModel.Design.DesignerVerbCollection> に追加されています。イベント ハンドラー コードも示します。  
  
```csharp  
public override DesignerVerbCollection Verbs  
{  
    get  
    {  
        if (m_verbs == null)  
        {  
            m_verbs = new DesignerVerbCollection();  
            m_verbs.Add(new DesignerVerb("Proportional Scaling", new EventHandler(OnProportionalScaling)));  
         m_verbs[0].Checked = (GetCustomProperty("poly:Proportional") == bool.TrueString);  
        }  
  
        return m_verbs;  
    }  
}  
  
private void OnProportionalScaling(object sender, EventArgs e)  
{  
   bool proportional = !  
        (GetCustomProperty("poly:Proportional") == bool.TrueString);  
   m_verbs[0].Checked = proportional;  
   SetCustomProperty("poly:Proportional", proportional.ToString());  
   ChangeService().OnComponentChanged(this, null, null, null);  
   Invalidate();  
}  
```  
  
### <a name="using-adornments"></a>装飾の使用  
 カスタム レポート アイテムのクラスに実装できるも、 **Microsoft.ReportDesigner.Design.Adornment**クラスです。 装飾を使用すると、カスタム レポート アイテムのコントロールで、デザイン画面のメインの四角形の外に領域を作成できます。 これらの領域では、マウス クリックやドラッグ アンド ドロップ操作などのユーザー インターフェイス イベントを扱うことができます。 **装飾**クラスで定義されている、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] **Microsoft.ReportDesigner**名前空間はのパススルー実装、<xref:System.Windows.Forms.Design.Behavior.Adorner>クラスは、Windows フォームで見つかりました。 完全なドキュメントについて、**装飾**クラスを参照してください[動作サービスの概要](http://go.microsoft.com/fwlink/?LinkId=116673)MSDN ライブラリです。 実装するサンプル コードについて、 **Microsoft.ReportDesigner.Design.Adornment**クラスを参照してください[SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] での Windows フォームを使ったプログラミングの詳細については、MSDN ライブラリの次のトピックを参照してください。  
  
-   コンポーネントのデザイン時属性  
  
-   内のコンポーネント[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]  
  
-   チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成  
  
## <a name="see-also"></a>参照  
 [カスタム レポート アイテムのアーキテクチャ](../../reporting-services/custom-report-items/custom-report-item-architecture.md)   
 [カスタム レポート アイテムの実行時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [カスタム レポート アイテムのクラス ライブラリ](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)   
 [方法: カスタム レポート アイテムを配置](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
  
  
