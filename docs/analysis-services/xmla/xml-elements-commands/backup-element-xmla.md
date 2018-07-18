---
title: 要素 (XMLA) のバックアップ |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4e00a4991226779a91e16806dbe15973d946ec69
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38007152"
---
# <a name="backup-element-xmla"></a>Backup 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  バックアップ ファイルを Analysis Services データベースをバックアップします。  
  
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
  
## <a name="element-relationships"></a>要素間のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Command](../../../analysis-services/xmla/xml-elements-properties/command-element-xmla.md)|  
|子要素|[AllowOverwrite](../../../analysis-services/xmla/xml-elements-properties/allowoverwrite-element-xmla.md)、 [ApplyCompression](../../../analysis-services/xmla/xml-elements-properties/applycompression-element-xmla.md)、 [BackupRemotePartitions](../../../analysis-services/xmla/xml-elements-properties/backupremotepartitions-element-xmla.md)、[ファイル](../../../analysis-services/xmla/xml-elements-properties/file-element-xmla.md)、[場所](../../../analysis-services/xmla/xml-elements-properties/locations-element-xmla.md)、 [オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)、[パスワード](../../../analysis-services/xmla/xml-elements-properties/password-element-xmla.md)、[セキュリティ](../../../analysis-services/xmla/xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 **バックアップ**コマンドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、[オブジェクト](../../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)バックアップ ファイル、および必要に応じてリモート バックアップ ファイルにリモート パーティションをバックアップする要素。 場合、**オブジェクト**以外の要素がオブジェクトを指す、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース、エラーが発生します。  
  
 **Backup** コマンドがバックアップする情報は、データベース内のオブジェクトが使用するストレージ モードによって異なります。 次の表は、ストレージ モードに応じてどの情報がバックアップされるかを示しています。  
  
|[ストレージ モード]|バックアップされる情報|  
|------------------|-----------------------------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 中に、**バックアップ**コマンド、共有ロックを設定、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、**オブジェクト**要素。 **Backup** コマンドの完了後、共有ロックは解放されます。  
  
 複数**バックアップ**でコマンドが含まれている場合は、並列でコマンドを実行できます、[並列](../../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)のコレクションを[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)コマンド。 **Parallel** コレクションを使用すると、同時に複数のバックアップ ファイルにデータベースをバックアップできます。  
  
 バックアップして、データベースの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、バックアップ コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所に対する書き込み権限を持っている必要があります。 また、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであるか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーであることが条件となります。  
  
## <a name="see-also"></a>参照
 [Restore 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/restore-element-xmla.md)   
 [Synchronize 要素&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/synchronize-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](../../../analysis-services/xmla/xml-elements-commands/xml-elements-commands.md)  
  
  
