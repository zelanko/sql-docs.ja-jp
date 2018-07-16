---
title: 要素 (XMLA) のバックアップ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Backup Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#Backup
- http://schemas.microsoft.com/analysisservices/2003/engine#Backup
- microsoft.xml.analysis.backup
helpviewer_keywords:
- Backup command
ms.assetid: 5bcbc14c-9db9-45b2-99de-f3a265bcb0c4
caps.latest.revision: 19
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a571681f52fb34e55df238229f659aa883bc84ac
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37215652"
---
# <a name="backup-element-xmla"></a>Backup 要素 (XMLA)
  バックアップ、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベースをバックアップ ファイルにします。  
  
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
|親要素|[Command](../xml-elements-properties/command-element-xmla.md)|  
|子要素|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md)、 [ApplyCompression](../xml-elements-properties/applycompression-element-xmla.md)、 [BackupRemotePartitions](../xml-elements-properties/backupremotepartitions-element-xmla.md)、[ファイル](../xml-elements-properties/file-element-xmla.md)、[場所](../xml-elements-properties/locations-element-xmla.md)、 [オブジェクト](../xml-elements-properties/object-element-xmla.md)、[パスワード](../xml-elements-properties/password-element-xmla.md)、[セキュリティ](../xml-elements-properties/security-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `Backup`コマンドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、[オブジェクト](../xml-elements-properties/object-element-xmla.md)バックアップ ファイル、および必要に応じてリモート バックアップ ファイルにリモート パーティションをバックアップする要素。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベース以外のオブジェクトを `Object` 要素が参照する場合、エラーが発生します。  
  
 どのような情報、`Backup`コマンドのバックアップを作成するデータベース内のオブジェクトで使用されるストレージ モードによって異なります。 次の表は、ストレージ モードに応じてどの情報がバックアップされるかを示しています。  
  
|[ストレージ モード]|バックアップされる情報|  
|------------------|-----------------------------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 中に、`Backup`コマンド、共有ロックを設定、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、`Object`要素。 共有ロックを解放した後、`Backup`コマンドが完了しました。  
  
 複数`Backup`でコマンドが含まれている場合は、並列でコマンドを実行できます、[並列](../xml-elements-properties/parallel-element-xmla.md)のコレクションを[バッチ](batch-element-xmla.md)コマンド。 `Parallel` コレクションを使用すると、同時に複数のバックアップ ファイルにデータベースをバックアップできます。  
  
 バックアップして、データベースの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、バックアップ コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所に対する書き込み権限を持っている必要があります。 また、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであるか、バックアップするデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーであることが条件となります。  
  
## <a name="see-also"></a>参照  
 [Restore 要素&#40;XMLA&#41;](restore-element-xmla.md)   
 [Synchronize 要素&#40;XMLA&#41;](synchronize-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
