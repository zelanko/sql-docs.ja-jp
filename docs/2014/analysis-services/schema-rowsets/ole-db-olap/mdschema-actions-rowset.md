---
title: MDSCHEMA_ACTIONS 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- MDSCHEMA_ACTIONS
topic_type:
- apiref
helpviewer_keywords:
- MDSCHEMA_ACTIONS rowset
ms.assetid: f73081f8-ac51-4286-b46e-2b34e792c3e0
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5b3e3a4c91d998e0ba0459577f1e0b469ec7f78b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36175838"
---
# <a name="mdschemaactions-rowset"></a>MDSCHEMA_ACTIONS 行セット
  クライアント アプリケーションで利用できるアクションについて記述します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `MDSCHEMA_ACTIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`||データベースの名前。|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`||サポートされていません。 常に `VT_NULL` を格納します。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||このアクションが所属するキューブの名前。|  
|`ACTION_NAME`|`DBTYPE_WSTR`||このアクションの名前。|  
|`ACTION_TYPE`|`DBTYPE_I4`||アクションのトリガー方法を指定するために使用されるビットマップ。 Msmd.h ファイルは、このビットマップに対して次のビット値定数を定義します。<br /><br /> -   `MDACTION_TYPE_URL` (`0x01`)<br />-   `MDACTION_TYPE_HTML` (`0x02`)<br />-   `MDACTION_TYPE_STATEMENT` (`0x04`)<br />-   `MDACTION_TYPE_DATASET` (`0x08`)<br />-   `MDACTION_TYPE_ROWSET` (`0x10`)<br />-   `MDACTION_TYPE_COMMANDLINE` (`0x20`)<br />-   `MDACTION_TYPE_PROPRIETARY` (`0x40`)<br />-   `MDACTION_TYPE_REPORT` (`0x80`)<br />-   `MDACTION_TYPE_DRILLTHROUGH` (`0x100`)|  
|`COORDINATE`|`DBTYPE_WSTR`||アクションが実行される多次元領域でオブジェクトまたは座標を指定する多次元式 (MDX)。 この制限列の値は、クライアント アプリケーションから提供される必要があります。<br /><br /> `CORDINATE` は、`COORDINATE_TYPE` で指定されたオブジェクトに解決される必要があります。|  
|`COORDINATE_TYPE`|`DBTYPE_I4`||`COORDINATE` 制限列の解釈方法を指定するビットマップ。 Msmd.h ファイルは、このビットマップに対して次のビット値定数を定義します。<br /><br /> -   `MDACTION_COORDINATE_CUBE` (`1`)<br />-   `MDACTION_COORDINATE_DIMENSION` (`2`)<br />     ディメンション階層を示します。<br />-   `MDACTION_COORDINATE_LEVEL` (`3`)<br />-   `MDACTION_COORDINATE_MEMBER` (`4`)<br />-   `MDACTION_COORDINATE_SET` (`5`)<br />-   `MDACTION_COORDINATE_CELL` (`6`)|  
|`ACTION_CAPTION`|`DBTYPE_WSTR`||キャプションと翻訳が DDL で指定されなかった場合は、アクション名。<br /><br /> キャプションまたは翻訳が指定され、`CaptionIsMDX` が False である場合は、次のいずれかの文字列になります。<br /><br /> 適切な言語の翻訳します。<br />指定した言語の翻訳が見つからなかった場合は-指定したキャプションです。<br />に翻訳が見つからなかった場合、アクション名およびキャプションが DDL で指定されていません。<br /><br /> キャプションまたは翻訳が指定され、`CaptionIsMDX` が True である場合は、指定した言語の適切な翻訳または DDL キャプションの指定した翻訳を見つけ、式を計算することによって生成される文字列。<br /><br /> アクションが MDX スクリプトで指定された場合、翻訳はなく、キャプションは常に MDX 式として扱われます。|  
|`DESCRIPTION`|`DBTYPE_WSTR`||アクションについてのわかりやすい説明。|  
|`CONTENT`|`DBTYPE_WSTR`||実行対象のアクションの式またはコンテンツ。|  
|`APPLICATION`|`DBTYPE_WSTR`||アクションを実行するために使用されるアプリケーションの名前。|  
|`INVOCATION`|`DBTYPE_I4`||アクションの呼び出し方法に関する情報。<br /><br /> -   `MDACTION_INVOCATION_INTERACTIVE` (`1`) 通常の操作中に使用される標準のアクションを示します。 この列の既定値です。<br />-   `MDACTION_INVOCATION_ON_OPEN` (`2`) キューブを最初に開いたときにアクションを実行することを示します。<br />-   `MDACTION_INVOCATION_BATCH` (`4`) アクションがバッチ操作の一部として実行されていることを示しますまたは[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]タスク。<br /><br /> これらの列挙値は、Msmd.h ファイルで定義されます。|  
  
 行セットは、`CATALOG_NAME`、`SCHEMA_NAME`、`CUBE_NAME`、`ACTION_NAME` を基準に並べ替えることができます。  
  
> [!NOTE]  
>  種類が `MDACTION_TYPE_PROPRIETARY` のアクションでは、`APPLICATION` 列の値を提供する必要があります。  
  
## <a name="restriction-columns"></a>制限の列  
 `MDSCHEMA_ACTIONS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`CATALOG_NAME`|`DBTYPE_WSTR`|省略可|  
|`SCHEMA_NAME`|`DBTYPE_WSTR`|省略可|  
|`CUBE_NAME`|`DBTYPE_WSTR`|必須|  
|`ACTION_NAME`|`DBTYPE_WSTR`|省略可|  
|`ACTION_TYPE`|`DBTYPE_I4`|省略可|  
|`COORDINATE`|`DBTYPE_WSTR`|必須|  
|`COORDINATE_TYPE`|`DBTYPE_I4`|必須|  
|`INVOCATION`|`DBTYPE_I4`|(省略可) `INVOCATION` 制限列の既定値は `MDACTION_INVOCATION_INTERACTIVE` です。 すべてのアクションを取得するには、`MDACTION_INVOCATION_ALL` 制限列で `INVOCATION` 値を使用します。|  
|`CUBE_SOURCE`|`DBTYPE_UI2`|(省略可) 次のいずれかの有効値を含むビットマップ。<br /><br /> -1 のキューブ<br />2 つのディメンション<br /><br /> 既定の制限の値は 1 です。|  
  
> [!IMPORTANT]  
>  `INVOCATION` 制限列の既定値は `MDACTION_INVOCATION_INTERACTIVE` です。 この列の値を明示的に指定しないスキーマ行セットには、この値を持つ行しか格納されません。 行セットにアクション セット全体を格納するには、`MDACTION_INVOCATION_ALL` 制限列で `INVOCATION` 定数を使用します。  
  
 クライアント アプリケーションは、OR 演算子を使用することによって複数の `ACTION_TYPE` を定義できます。  
  
## <a name="remarks"></a>コメント  
 次の表は、`COORDINATE` と `COORDINATE_TYPE` の有効な組み合わせの一覧です。  
  
|COORDINATE オブジェクトの種類|COORDINATE_TYPE|  
|----------------------------|----------------------|  
|`Cube`|`MDACTION_COORDINATE_CUBE`|  
|`Dimension`|`MDACTION_COORDINATE_DIMENSION`<br /><br /> `MDACTION_COORDINATE_LEVEL`<br /><br /> `MDACTION_COORDINATE_MEMBER`<br /><br /> `MDACTION_COORDINATE_SET`<br /><br /> `MDACTION_COORDINATE_CELL`|  
|`Hierarchy`|`MDACTION_COORDINATE_DIMENSION`|  
|`Level`|`MDACTION_COORDINATE_LEVEL`|  
|`Member`|`MDACTION_COORDINATE_MEMBER`|  
|`Set`|`MDACTION_COORDINATE_SET`|  
|`cell`|`MDACTION_COORDINATE_CELL`|  
  
## <a name="see-also"></a>参照  
 [OLE DB for OLAP Schema 行セット](ole-db-for-olap-schema-rowsets.md)  
  
  