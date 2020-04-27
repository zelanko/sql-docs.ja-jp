---
title: '[アセンブリのプロパティ] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.assemblyproperties.f1
ms.assetid: da1174d6-d82b-4337-ac19-7368dbd95a84
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b21230ddff5a3db043b533a4f921a30b02da739b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66062295"
---
# <a name="assembly-properties-dialog-box-analysis-services---multidimensional-data"></a>[アセンブリのプロパティ] ダイアログ ボックス (Analysis Services - 多次元データ)
  **の** [アセンブリのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのアセンブリ参照のプロパティを設定できます。 **[アセンブリのプロパティ]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** でアセンブリを右クリックして **[プロパティ]** をクリックします。  
  
## <a name="options"></a>オプション  
  
|用語|定義|  
|----------|----------------|  
|**名前**|変更するアセンブリ参照の名前を入力します。<br /><br /> 注: この値を変更しても、アセンブリ参照が参照するアセンブリの名前は変更されませんが、アセンブリ参照を参照する際に [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスまたはデータベースが使用する名前が変更されます。|  
|**ID**|アセンブリ参照が参照するアセンブリの ID を表示します。|  
|**説明**|変更するアセンブリ参照の説明を入力します。|  
|**[タイムスタンプの作成]**|アセンブリ参照が作成された日時を表示します。|  
|**[スキーマの最終更新]**|アセンブリ参照のメタデータが最後に更新された日時を表示します。|  
|**Type**|アセンブリ参照の種類を表示します。 次の値が表示されます。<br /><br /> **.Net アセンブリ**: アセンブリ参照は[!INCLUDE[msCoName](../includes/msconame-md.md)] .NET Framework アセンブリを参照します。<br /><br /> **COM DLL**: アセンブリ参照は com ライブラリを参照します。|  
|**ソース**|アセンブリ参照のソースを表示します。 このプロパティは通常、アセンブリ参照が参照するアセンブリの完全なパスおよびファイル名を含んでいます。|  
|**[権限セット]**|アセンブリ参照へのアクセスの決定に使用される権限セットを選択します。 このプロパティで使用できる値の詳細については<xref:Microsoft.AnalysisServices.ClrAssembly.PermissionSet%2A>、「」を参照してください。|  
|**[権限借用情報]**|アセンブリ参照へのアクセス時に使用する権限借用情報を選択します。 このプロパティで使用可能な値の詳細については、「[ImpersonationInfo 要素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/impersonationinfo-element-assl)」をご覧ください。|  
  
## <a name="see-also"></a>参照  
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [多次元モデルのアセンブリの管理](multidimensional-models/multidimensional-model-assemblies-management.md)  
  
  
