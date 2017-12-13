---
title: "バックアップの要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: Backup Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords: Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: "19"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 26a67121b506f33f69b408fde57aa2e94fa3beed
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="backup-element-xmla"></a>Backup 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]バックアップ、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースをバックアップ ファイル。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Backup>  
      <Object>...</Object>  
      <File>...</File>  
      <Security>...</Security>  
      <ApplyCompression>...</ApplyCompression>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <BackupRemotePartitions>...</BackupRemotePartitions>  
      <Locations>...</Locations>  
   </Backup>  
</Command>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)、 [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md)、 [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)、[ファイル](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)、 [オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、[パスワード](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)、[セキュリティ](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **バックアップ**コマンド バックアップ、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)要素をバックアップ ファイル、および必要に応じてリモート バックアップ ファイルにリモート パーティションをバックアップします。 場合、**オブジェクト**要素を指すオブジェクト以外の場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース、エラーが発生します。  
  
 **Backup** コマンドがバックアップする情報は、データベース内のオブジェクトが使用するストレージ モードによって異なります。 次の表は、ストレージ モードに応じてどの情報がバックアップされるかを示しています。  
  
|[ストレージ モード]|バックアップされる情報|  
|------------------|-----------------------------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 中に、**バックアップ**コマンドに共有ロックがかけ、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、**オブジェクト**要素。 **Backup** コマンドの完了後、共有ロックは解放されます。  
  
 複数**バックアップ**でコマンドが含まれている場合は、並列でコマンドを実行できます、[並列](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)のコレクション、[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンド。 **Parallel** コレクションを使用すると、同時に複数のバックアップ ファイルにデータベースをバックアップできます。  
  
 バックアップと復元、データベースの詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期 (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md).  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、バックアップ コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所に対する書き込み権限を持っている必要があります。 また、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであるか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーであることが条件となります。  
  
## <a name="see-also"></a>参照  
 [要素 &#40; を復元します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [要素 &#40; を同期します。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [コマンドと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
