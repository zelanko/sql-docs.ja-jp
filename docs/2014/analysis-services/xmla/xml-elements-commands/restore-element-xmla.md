---
title: Restore 要素 (XMLA) |Microsoft Docs
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
- Restore Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#Restore
- urn:schemas-microsoft-com:xml-analysis#Restore
- microsoft.xml.analysis.restore
helpviewer_keywords:
- Restore command
ms.assetid: bb5a0c92-3927-4fa4-975b-6e4d79e0a912
caps.latest.revision: 26
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 682806680604606d54c133617b2150b975cf8c03
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37275658"
---
# <a name="restore-element-xmla"></a>Restore 要素 (XMLA)
  復元を[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]データベース バックアップ ファイルから。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Command>  
   <Restore>  
      <DatabaseName>...</DatabaseName>  
      <DatabaseID>...</DatabaseID>  
      <File>...</File>  
      <Security>...</Security>  
      <AllowOverwrite>...</AllowOverwrite>  
      <Password>...</Password>  
      <Locations>...</Locations>  
      <DbStorageLocation>...</DbStorageLocation>  
   </Restore>  
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
|子要素|[AllowOverwrite](../xml-elements-properties/allowoverwrite-element-xmla.md)、 [DatabaseName](../xml-elements-properties/name-element-xmla.md)、 [DatabaseID](../xml-elements-properties/id-element-xmla.md)、[ファイル](../xml-elements-properties/file-element-xmla.md)、[場所](../xml-elements-properties/locations-element-xmla.md)、[パスワード](../xml-elements-properties/password-element-xmla.md)、[セキュリティ](../xml-elements-properties/security-element-xmla.md)、 [DbStorageLocation](../xml-elements-properties/dbstoragelocation-element.md)|  
  
## <a name="remarks"></a>コメント  
 `Restore`コマンドは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、`DatabaseName`要素からバックアップ ファイルと、必要に応じてリモート バックアップ ファイルからリモート パーティションを復元します。  
  
 バックアップのファイルに格納されているオブジェクトによって使用されるストレージ モードに応じて、`Restore`コマンドは、次の表に示すように情報を復元します。  
  
|[ストレージ モード]|[情報]|  
|------------------|-----------------|  
|多次元 OLAP (MOLAP)|ソース データ、集計、およびメタデータ|  
|ハイブリッド OLAP (HOLAP)|集計とメタデータ|  
|リレーショナル OLAP (ROLAP)|メタデータ|  
  
 中に、`Restore`コマンドに対して、排他ロックが設定されます、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]で指定されたデータベース、`DatabaseName`要素。 ロックが解放した後、`Restore`コマンドが完了しました。  
  
 バックアップして、データベースの復元の詳細については、次を参照してください。[データベースのバックアップ、復元、およびデータベースの同期&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)します。  
  
> [!IMPORTANT]  
>  バックアップ ファイルごとに、復元コマンドを実行するユーザーは、各ファイルに指定されたバックアップ場所から読み取る権限を持っている必要があります。 サーバーにインストールされていない [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースを復元する場合、ユーザーは、その [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーであることも必要です。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] データベースを上書きするには、ユーザーは、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスのサーバー ロールのメンバーか、復元するデータベースに対してフル コントロール (管理者) 権限を持つデータベース ロールのメンバーのいずれかである必要があります。  
  
> [!NOTE]  
>  既存のデータベースを復元すると、データベースを復元したユーザーは、復元されたデータベースにアクセスできなくなる可能性があります。 バックアップの実行時に、ユーザーがサーバー ロールのメンバー、またはフル コントロール (管理者) 権限を持つデータベース ロールのメンバーではなかった場合、このようにアクセスできなくなることがあります。  
  
## <a name="see-also"></a>参照  
 [バックアップ要素&#40;XMLA&#41;](backup-element-xmla.md)   
 [要素をバッチ&#40;XMLA&#41;](batch-element-xmla.md)   
 [要素を並列&#40;XMLA&#41;](../xml-elements-properties/parallel-element-xmla.md)   
 [Synchronize 要素&#40;XMLA&#41;](synchronize-element-xmla.md)   
 [コマンド&#40;XMLA&#41;](xml-elements-commands.md)  
  
  
