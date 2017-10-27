---
title: "カスタム レポート アイテムのクラス ライブラリ |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
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
- custom report items, RDL
- RDL [Reporting Services], custom report items
ms.assetid: f18c5d8f-1d6b-4f0b-8657-c14896c2ce0d
caps.latest.revision: 27
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f216228c01e835e88cd9d4c7d7d4190648a386db
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="custom-report-item-class-libraries"></a>カスタム レポート アイテムのクラス ライブラリ
  カスタム レポート アイテムからクラスを使用して、 **Microsoft.ReportDesigner**名前空間。 カスタム レポート アイテムを実装する際に使用するクラスは、2 つの主なカテゴリに分類できます。1 つは、カスタム レポート アイテム インフラストラクチャをサポートするためにデザインされた独自のクラス、もう 1 つは、関連するレポート定義言語 (RDL) 要素の機能をカプセル化するマネージ ラッパー クラスです。 これらのクラスを使用する方法のコード サンプルは、次を参照してください。 [SQL Server Reporting Services Product Samples](http://go.microsoft.com/fwlink/?LinkId=177889)です。  
  
## <a name="custom-report-item-infrastructure-classes"></a>カスタム レポート アイテム インフラストラクチャのクラス  
 以下のクラスは、カスタム レポート アイテムを実装するために使用されます。  
  
> [!NOTE]  
>  以下の各表はすべてを網羅したものではなく、各クラスの最も一般的に使用されるプロパティやメソッドのみが含まれています。  
  
### <a name="microsoftreportdesignercustomreportitemdesigner"></a>Microsoft.ReportDesigner.CustomReportItemDesigner  
 カスタム レポート アイテムのメイン クラスです。 カスタム レポート アイテムの実装のメイン クラスは、このクラスを継承する必要があります。  
  
#### <a name="public-properties"></a>パブリック プロパティ  
  
|||  
|-|-|  
|**名前**|カスタム レポート アイテムの名前|  
|**型**|カスタム レポート アイテムの種類。|  
|**CustomData**|デザイン時に指定されたカスタム レポート アイテムのデータ プロパティをカプセル化する <xref:Microsoft.ReportingServices.RdlObjectModel.CustomData> オブジェクト|  
|**CustomProperties**|カスタム レポート アイテムのカスタム プロパティのコレクション|  
|**高さ**|カスタム レポート アイテム コントロールの高さ|  
|**幅**|カスタム レポート アイテム コントロールの幅|  
|**レポート**|レポート レベルのプロパティ (レポートのデータセットの一覧など) のコンテナー|  
|**AltReportItem**|カスタム レポート アイテムの実行時コントロールがサポートされていない場合に使用される代替レポート アイテム オブジェクト|  
|**スタイル**|カスタム レポート アイテムのスタイルのプロパティ|  
|**表示要素**|コントロールのインタラクティブな編集のために使用される装飾ウィンドウ|  
|**サイト**|**ISite**のコンポーネントです。|  
|**DesignerVerbCollection**|コントロールのショートカット メニューのカスタム動詞の配列|  
  
#### <a name="public-methods"></a>パブリック メソッド  
  
|||  
|-|-|  
|**BeginEdit**|コントロールのインタラクティブな編集をアクティブにします。|  
|**DoDefaultAction**|コントロールをダブルクリックしたとき、またはコントロールに対して Enter キーを押したときに呼び出されます。|  
|**EndEdit**|コントロールのインタラクティブな編集を非アクティブにします。|  
|**GetService**|サービスを表すオブジェクトを返します。|  
|**InitializeNewComponent**|新しいカスタム レポート アイテムの作成時に呼び出されます。|  
|**無効化します。**|コントロールの表面全体を再描画します。|  
|**OnDragEnter**<br /><br /> **OnDragDrop**|オブジェクトをコントロールにドラッグすると呼び出されます。|  
|**OnPaint**|応答と呼ばれる、**ペイント**イベント。|  
  
### <a name="microsoftreportdesignercustomreportitemattribute"></a>Microsoft.ReportDesigner.CustomReportItemAttribute  
 この属性は、カスタム レポート アイテムの種類を識別するために使用されます。 名前の値に一致する必要があります、 \<**名前**> の属性、 **ReportItem**レポート デザイナー構成ファイル内の要素。  
  
#### <a name="public-methods"></a>パブリック メソッド  
  
|||  
|-|-|  
|**CustomReportItemAttribute**|CustomReportItemAttribute オブジェクトを構築します。|  
  
### <a name="microsoftreportdesignerlocalizednameattribute"></a>Microsoft.ReportDesigner.LocalizedNameAttribute  
 この属性は、カスタム レポート アイテム デザイナーで使用する表示名を指定するために使用されます。  
  
#### <a name="public-methods"></a>パブリック メソッド  
  
|||  
|-|-|  
|**LocalizedNameAttribute**|LocalizedNameAttribute オブジェクトを構築します。|  
  
### <a name="microsoftreportdesigneradornment"></a>Microsoft.ReportDesigner.Adornment  
 **装飾**クラスは、デザイン画面のメインの四角形の外部で領域を提供するカスタム レポート アイテムのデザイン時コンポーネントによって使用されます。 これらの領域では、マウス クリックやドラッグ アンド ドロップ操作などのユーザー インターフェイス イベントを扱うことができます。  
  
#### <a name="public-methods"></a>パブリック メソッド  
  
|||  
|-|-|  
|**OnShow**|ときに呼び出されます、**装飾**がアクティブ化します。|  
|**OnHide**|ときに呼び出されます、**装飾**が非アクティブ化します。|  
|**ペイント**|応答と呼ばれる、**ペイント**イベント。|  
|**OnDragEnter**<br /><br /> **OnDragOver**<br /><br /> **OnDragLeave**<br /><br /> **OnDragDrop**|オブジェクトがドラッグされるときに呼び出されます、**装飾**です。|  
  
### <a name="microsoftreportdesigneradornerservice"></a>Microsoft.ReportDesigner.AdornerService  
 このクラスは、サポートするために、カスタム レポート アイテムによって使用される表示サービスのコレクションを提供する使用**装飾**カスタム レポート アイテムのデザイン時コンポーネントのオブジェクト。  
  
#### <a name="public-properties"></a>パブリック プロパティ  
  
|||  
|-|-|  
|**AdornerWindowBounds**|Adorner ウィンドウの境界|  
|**AdornerWindowRegion**|Adorner ウィンドウの領域|  
|**AdornerWindowGraphics**|Adorner ウィンドウのグラフィック コンテキスト|  
  
#### <a name="public-methods"></a>パブリック メソッド  
  
|||  
|-|-|  
|**ComponentRectInDesignerFrame**|デザイナー フレームの座標に変換されたコンポーネントの境界を返します。|  
|**InvalidateAdorner**|Adorner ウィンドウを無効にします。|  
|**PointToAdorner**|Adorner ウィンドウの座標に変換された画面座標の点を返します。|  
  
### <a name="microsoftreportdesignerexpressioneditor"></a>Microsoft.ReportDesigner.ExpressionEditor  
 このクラスは、カスタム レポート アイテムのデザイン時コントロールから式エディターを呼び出すために使用できます。  
  
#### <a name="public-methods"></a>パブリック メソッド  
  
|||  
|-|-|  
|**EditValue**|式エディターを呼び出して、渡されたオブジェクト値で初期化します。|  
  
### <a name="microsoftreportdesignerifieldsdataobject"></a>Microsoft.ReportDesigner.IFieldsDataObject  
 このクラスは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] フィールドのコレクションであり、デザイン環境でドラッグ アンド ドロップ イベントをサポートするために使用されます。 継承**IReportItemDataObject**です。  
  
#### <a name="public-properties"></a>パブリック プロパティ  
  
|||  
|-|-|  
|**DataSetName**|ドロップされるフィールドを含むデータセットの名前|  
|**フィールド**|フィールドのコレクション (**Microsoft.ReportDesigner.Field**) を削除します。|  
  
## <a name="see-also"></a>参照  
 [レポート定義言語 & #40 です。SSRS &#41;](../../reporting-services/reports/report-definition-language-ssrs.md)   
 [カスタム レポート アイテムの実行時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)   
 [カスタム レポート アイテムのデザイン時コンポーネントの作成](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)  
  
  

