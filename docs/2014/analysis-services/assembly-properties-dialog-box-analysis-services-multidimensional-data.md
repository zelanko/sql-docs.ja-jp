---
title: アセンブリのプロパティ ダイアログ ボックス (Analysis Services - 多次元データ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: fa00c8753e30926113d90881401a8b38e573e6b8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085337"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>[アセンブリのプロパティ] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [アセンブリのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのアセンブリ参照のプロパティを設定できます。 **[アセンブリのプロパティ]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** でアセンブリを右クリックして **[プロパティ]** をクリックします。  
  
## <a name="options"></a>および  
  
|項目|定義|  
|----------|----------------|  
|**Name**|変更するアセンブリ参照の名前を入力します。<br /><br /> 注: この値を変更しても、アセンブリ参照が参照するアセンブリの名前は変更されませんが、アセンブリ参照を参照する際に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスまたはデータベースが使用する名前が変更されます。|  
|**ID**|アセンブリ参照が参照するアセンブリの ID を表示します。|  
|**description**|変更するアセンブリ参照の説明を入力します。|  
|**[タイムスタンプの作成]**|アセンブリ参照が作成された日時を表示します。|  
|**[スキーマの最終更新]**|アセンブリ参照のメタデータが最後に更新された日時を表示します。|  
|**Type**|アセンブリ参照の種類を表示します。 次の値が表示されます。<br /><br /> **.NET アセンブリ**: アセンブリ参照が指す、 [!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework アセンブリ。<br /><br /> **COM DLL**: アセンブリ参照は COM ライブラリを参照します。|  
|**Source**|アセンブリ参照のソースを表示します。 このプロパティは通常、アセンブリ参照が参照するアセンブリの完全なパスおよびファイル名を含んでいます。|  
|**権限セット**|アセンブリ参照へのアクセスの決定に使用される権限セットを選択します。 このプロパティの使用可能な値の詳細については、次を参照してください。<xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>です。|  
|**[権限借用情報]**|アセンブリ参照へのアクセス時に使用する権限借用情報を選択します。 このプロパティで使用可能な値の詳細については、「[ImpersonationInfo 要素 &#40;ASSL&#41;](scripting/properties/impersonationinfo-element-assl.md)」をご覧ください。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [多次元モデルのアセンブリの管理](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  