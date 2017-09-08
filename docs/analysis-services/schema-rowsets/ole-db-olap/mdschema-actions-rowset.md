---
title: "MDSCHEMA_ACTIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MDSCHEMA_ACTIONS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e9abd044460f463b952eb6fbd88cd7d7a4ea2821
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="mdschemaactions-rowset"></a>MDSCHEMA_ACTIONS 行セット
  クライアント アプリケーションで利用できるアクションについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 **MDSCHEMA_ACTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**||データベースの名前。|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**||サポートされていません。 常に含まれています。 **vt_**です。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||このアクションが所属するキューブの名前。|  
|**ACTION_NAME**|**DBTYPE_WSTR**||このアクションの名前。|  
|**ACTION_TYPE**|**DBTYPE_I4**||アクションのトリガー方法を指定するために使用されるビットマップ。 Msmd.h ファイルは、このビットマップに対して次のビット値定数を定義します。<br /><br /> **MDACTION_TYPE_URL** (**0x01**)<br /><br /> **MDACTION_TYPE_HTML** (**0x02**)<br /><br /> **MDACTION_TYPE_STATEMENT** (**0x04**)<br /><br /> **MDACTION_TYPE_DATASET** (**0x08**)<br /><br /> **MDACTION_TYPE_ROWSET** (**0x10**)<br /><br /> **MDACTION_TYPE_COMMANDLINE** (**0x20**)<br /><br /> **MDACTION_TYPE_PROPRIETARY** (**0x40**)<br /><br /> **MDACTION_TYPE_REPORT** (**0x80**)<br /><br /> **MDACTION_TYPE_DRILLTHROUGH** (**0x100**)|  
|**座標**|**DBTYPE_WSTR**||アクションが実行される多次元領域でオブジェクトまたは座標を指定する多次元式 (MDX)。 この制限列の値は、クライアント アプリケーションから提供される必要があります。<br /><br /> **CORDINATE**で指定されたオブジェクトに解決する必要があります**COORDINATE_TYPE**です。|  
|**COORDINATE_TYPE**|**DBTYPE_I4**||ビットマップを指定する方法、**調整**制限列の解釈します。 Msmd.h ファイルは、このビットマップに対して次のビット値定数を定義します。<br /><br /> **MDACTION_COORDINATE_CUBE** (**1**)<br /><br /> **MDACTION_COORDINATE_DIMENSION** (**2**): ディメンション階層を指します。<br /><br /> **MDACTION_COORDINATE_LEVEL** (**3**)<br /><br /> **MDACTION_COORDINATE_MEMBER** (**4**)<br /><br /> **MDACTION_COORDINATE_SET** (**5**)<br /><br /> **MDACTION_COORDINATE_CELL** (**6**)|  
|**ACTION_CAPTION**|**DBTYPE_WSTR**||キャプションと翻訳が DDL で指定されなかった場合は、アクション名。<br /><br /> キャプションまたは翻訳、指定した場合と**CaptionIsMDX**が false の場合、次の文字列のいずれか。<br /><br /> 適切な言語の翻訳します。<br /><br /> 指定した言語の翻訳が見つからなかった場合は-指定したキャプションです。<br /><br /> に翻訳が見つからなかった場合、アクション名およびキャプションが DDL で指定されていません。<br /><br /> キャプションまたは翻訳、指定した場合と**CaptionIsMDX**から指定された言語または DDL キャプションの指定の平行移動の適切な翻訳を検索して、計算結果の文字列が true の場合、文字列を作成する数式です。<br /><br /> アクションが MDX スクリプトで指定された場合、翻訳はなく、キャプションは常に MDX 式として扱われます。|  
|**DESCRIPTION**|**DBTYPE_WSTR**||アクションについてのわかりやすい説明。|  
|**コンテンツ**|**DBTYPE_WSTR**||実行対象のアクションの式またはコンテンツ。|  
|**アプリケーション**|**DBTYPE_WSTR**||アクションを実行するために使用されるアプリケーションの名前。|  
|**呼び出し**|**DBTYPE_I4**||アクションの呼び出し方法に関する情報。<br /><br /> **MDACTION_INVOCATION_INTERACTIVE** (**1**) 通常の操作中に使用される標準のアクションを示します。 この列の既定値です。<br /><br /> **MDACTION_INVOCATION_ON_OPEN** (**2**) キューブを最初に開いたときにアクションを実行することを示します。<br /><br /> **MDACTION_INVOCATION_BATCH** (**4**) アクションがバッチ操作の一部として実行されていることを示しますまたは[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]タスク。<br /><br /> <br /><br /> これらの列挙値が Msmd.h ファイルで定義されていることに注意してください。|  
  
 行セットが並べ替えられて**CATALOG_NAME**、 **SCHEMA_NAME**、 **CUBE_NAME**、 **ACTION_NAME**です。  
  
> [!NOTE]  
>  アクションの**MDACTION_TYPE_PROPRIETARY**型の値を指定する必要があります、**アプリケーション**列です。  
  
## <a name="restriction-columns"></a>制限の列  
 **MDSCHEMA_ACTIONS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**CATALOG_NAME**|**DBTYPE_WSTR**|省略可|  
|**SCHEMA_NAME**|**DBTYPE_WSTR**|省略可|  
|**CUBE_NAME**|**DBTYPE_WSTR**|必須|  
|**ACTION_NAME**|**DBTYPE_WSTR**|省略可|  
|**ACTION_TYPE**|**DBTYPE_I4**|省略可|  
|**座標**|**DBTYPE_WSTR**|必須|  
|**COORDINATE_TYPE**|**DBTYPE_I4**|必須|  
|**呼び出し**|**DBTYPE_I4**|(省略可能)**呼び出し**制限列の値に既定値は**MDACTION_INVOCATION_INTERACTIVE**です。 すべてのアクションを取得するを使用して、 **MDACTION_INVOCATION_ALL**値で、**呼び出し**制限列です。|  
|**CUBE_SOURCE**|**DBTYPE_UI2**|(省略可能)既定の制限は、1 の値です。 有効な値は次のいずれかのビットマップ。<br /><br /> 1 キューブ<br /><br /> 2 ディメンション|  
  
> [!IMPORTANT]  
>  **呼び出し**制限列には、既定値は**MDACTION_INVOCATION_INTERACTIVE**です。 この列の値を明示的に指定しないスキーマ行セットには、この値を持つ行しか格納されません。 アクションのセット全体を格納する行セットを実行する場合に、使用、 **MDACTION_INVOCATION_ALL**の定数、**呼び出し**制限列です。  
  
 クライアント アプリケーションには、1 つ以上定義できます**ACTION_TYPE** OR 演算子を使用します。  
  
## <a name="remarks"></a>解説  
 次の表は、有効な一覧**調整**と**COORDINATE_TYPE**の組み合わせ。  
  
|COORDINATE オブジェクトの種類|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|**Cube**|**MDACTION_COORDINATE_CUBE**|  
|**Dimension**|**MDACTION_COORDINATE_DIMENSION**<br /><br /> **MDACTION_COORDINATE_LEVEL**<br /><br /> **MDACTION_COORDINATE_MEMBER**<br /><br /> **MDACTION_COORDINATE_SET**<br /><br /> **MDACTION_COORDINATE_CELL**|  
|**Hierarchy**|**MDACTION_COORDINATE_DIMENSION**|  
|**Level**|**MDACTION_COORDINATE_LEVEL**|  
|**メンバー**|**MDACTION_COORDINATE_MEMBER**|  
|**設定**|**MDACTION_COORDINATE_SET**|  
|**セル**|**MDACTION_COORDINATE_CELL**|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP スキーマ行セット](../../../analysis-services/schema-rowsets/ole-db-olap/ole-db-for-olap-schema-rowsets.md)  
  
  
