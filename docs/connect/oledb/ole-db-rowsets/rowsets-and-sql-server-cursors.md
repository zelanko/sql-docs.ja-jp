---
title: 行セットと SQL Server カーソル |Microsoft ドキュメント
description: 行セットと SQL Server カーソル
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-rowsets
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB rowsets, cursors
- OLE DB Driver for SQL Server, rowsets
- rowsets [OLE DB], cursors
- properties [OLE DB]
- cursors [OLE DB]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 94c2de4cdd2ef7edda0af15b4908781c4872c25c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="rowsets-and-sql-server-cursors"></a>行セットと SQL Server カーソル
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、2 種類の方法でコンシューマーに結果セットが返されます。  
  
-   既定の結果セット。これには次の特徴があります。  
  
    -   オーバーヘッドを最小限に抑えます。  
  
    -   最高のパフォーマンスでデータをフェッチします。  
  
    -   既定の順方向専用かつ読み取り専用のカーソル機能だけをサポートします。  
  
    -   一度に 1 行をコンシューマーに返します。  
  
    -   1 つの接続でサポートされるアクティブ ステートメントは一度に 1 つだけです。  
  
         ステートメントの実行後は、コンシューマーがすべての結果を取得するまで、またはステートメントが取り消されるまで、その接続で別のステートメントを実行することはできません。  
  
    -   すべての [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントをサポートします。  
  
-   サーバー カーソル。これには、次の特徴があります。  
  
    -   すべてのカーソル機能をサポートします。  
  
    -   コンシューマーに行のブロックを返すことができます。  
  
    -   1 つの接続で複数のアクティブ ステートメントをサポートします。  
  
    -   カーソル機能とパフォーマンスのバランスが取れています。  
  
         カーソル機能をサポートすると、既定の結果セットに比べてパフォーマンスが低下する場合があります。 コンシューマーはカーソル機能を使用して比較的小さな行のセットを取得することで、この欠点を補うことができます。  
  
    -   複数の結果セットを返す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントはサポートしません。  
  
 コンシューマーは、特定の行セット プロパティを設定することで、行セットでのカーソルの動作を変更できます。 コンシューマーは、これらの行セット プロパティのいずれかを設定しませんまたはすべての既定値に設定、SQL Server の OLE DB Driver は既定の結果セットを使用して行セットを実装します。 これらのプロパティのいずれかが、既定以外の値に設定されている場合、SQL Server の OLE DB Driver は、サーバー カーソルを使用して行セットを実装します。  
  
 次の行セット プロパティを使用する SQL Server の OLE DB Driver の直接[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソル。 プロパティによっては、他のプロパティと組み合わせて使用できるものもあります。 たとえば、DBPROP_IRowsetScroll プロパティと DBPROP_IRowsetChange プロパティを備えた行セットは、即時更新動作を表すブックマーク行セットになります。 同時に指定できないプロパティもあります。 たとえば、DBPROP_OTHERINSERT を備えた行セットにはブックマークを含めることはできません。  
  
|プロパティ ID|値|行セットの動作|  
|-----------------|-----------|---------------------|  
|DBPROP_SERVERCURSOR|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットは順次処理され、順方向のスクロールとフェッチのみがサポートされます。 相対行位置指定がサポートされます。 コマンド テキストに ORDER BY 句を指定できます。|  
|DBPROP_CANSCROLLBACKWARDS または DBPROP_CANFETCHBACKWARDS|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットでは、両方向へのスクロールとフェッチがサポートされます。 相対行位置指定がサポートされます。 コマンド テキストに ORDER BY 句を指定できます。|  
|DBPROP_BOOKMARKS または DBPROP_LITERALBOOKMARKS|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットは順次処理され、順方向のスクロールとフェッチのみがサポートされます。 相対行位置指定がサポートされます。 コマンド テキストに ORDER BY 句を指定できます。|  
|DBPROP_OWNUPDATEDELETE、DBPROP_OWNINSERT、または DBPROP_OTHERUPDATEDELETE|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットでは、両方向へのスクロールとフェッチがサポートされます。 相対行位置指定がサポートされます。 コマンド テキストに ORDER BY 句を指定できます。|  
|DBPROP_OTHERINSERT|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットでは、両方向へのスクロールとフェッチがサポートされます。 相対行位置指定がサポートされます。 参照先の列にインデックスが存在する場合は、コマンド テキストに ORDER BY 句を指定できます。<br /><br /> 行セットにブックマークが含まれる場合は、DBPROP_OTHERINSERT に VARIANT_TRUE を指定できません。 この表示設定プロパティとブックマークを指定して行セットを作成しようとすると、エラーが発生します。|  
|DBPROP_IRowsetLocate または DBPROP_IRowsetScroll|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットでは、両方向へのスクロールとフェッチがサポートされます。 ブックマークとを通じて絶対位置指定、 **IRowsetLocate**インターフェイスが、行セットでサポートされます。 コマンド テキストに ORDER BY 句を指定できます。<br /><br /> DBPROP_IRowsetLocate と DBPROP_IRowsetScroll は、行セット内にブックマークを要求します。 ブックマークを含み、DBPROP_OTHERINSERT に VARIANT_TRUE を設定した行セットを作成しようとすると、エラーが発生します。|  
|DBPROP_IRowsetChange または DBPROP_IRowsetUpdate|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できます。 行セットは順次処理され、順方向のスクロールとフェッチのみがサポートされます。 相対行位置指定がサポートされます。 更新可能なカーソルをサポートするすべてのコマンドでは、これらのインターフェイスがサポートされます。|  
|DBPROP_IRowsetLocate または DBPROP_IRowsetScroll、および DBPROP_IRowsetChange または DBPROP_IRowsetUpdate|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できます。 行セットでは、両方向へのスクロールとフェッチがサポートされます。 ブックマークとを通じて絶対位置指定**IRowsetLocate**行セットではサポートされています。 コマンド テキストに ORDER BY 句を指定できます。|  
|DBPROP_IMMOBILEROWS|VARIANT_FALSE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットでは、順方向のスクロールしかサポートされません。 相対行位置指定がサポートされます。 参照先の列にインデックスが存在する場合は、コマンド テキストに ORDER BY 句を指定できます。<br /><br /> DBPROP_IMMOBILEROWS は、別のセッションのコマンドや別のユーザーから挿入された [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 行を表示できる行セットだけで使用できます。 DBPROP_OTHERINSERT に VARIANT_TRUE を設定できない行セットで、プロパティに VARIANT_FALSE が設定されている行セットを開こうとすると、エラーが発生します。|  
|DBPROP_REMOVEDELETED|VARIANT_TRUE|行セットを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データを更新できません。 行セットでは、順方向のスクロールしかサポートされません。 相対行位置指定がサポートされます。 別のプロパティで制約されている場合を除いて、コマンド テキストに ORDER BY 句を指定できます。|  
  
 OLE DB 用のドライバーをサーバー カーソルでサポートされている SQL Server の行セットを簡単にで作成できる、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]ベース テーブルまたはビューを使用して、 **iopenrowset::openrowset**メソッドです。 名前によって、テーブルまたはビューを指定のプロパティ設定の必要な行セットを渡して、 *rgPropertySets*パラメーター。  
  
 コンシューマーが、サーバー カーソルでサポートされる行セットを要求すると、行セットを作成するコマンド テキストが制限されます。 具体的には、1 つの行セットを結果として返す 1 つの SELECT ステートメント、または 1 つの行セットを結果として返す 1 つの SELECT ステートメントを実装するストアド プロシージャに制限されます。  
  
 次の 2 つの表に、各種 OLE DB プロパティとカーソル モデルのマッピングを示します。 また、特定の種類のカーソル モデルを使用するために設定する必要がある行セット プロパティも示します。  
  
 表の各欄には、特定のカーソル モデル向けの行セット プロパティ値を示しています。 このトピックの前半で示した行セット プロパティのデータ型はすべて VT_BOOL で、既定値は VARIANT_FALSE です。 表では、次の記号を使用しています。  
  
 F = 既定値 (VARIANT_FALSE)  
  
 T = VARIANT_TRUE  
  
 \- = VARIANT_TRUE or VARIANT_FALSE  
  
 特定の種類のカーソル モデルを使用するには、カーソル モデルに対応する列を探し、列の値が "T" であるすべての行セット プロパティを見つけます。 これらの行セット プロパティに VARIANT_TRUE を設定すると、その特定のカーソル モデルを使用できます。 値が "-" の行セット プロパティには、VARIANT_TRUE と VARIANT_FALSE のどちらも設定できます。  
  
|行セット プロパティ/カーソル モデル|既定値<br /><br /> result<br /><br /> セット (set)<br /><br /> (RO)|[高速]<br /><br /> 順方向<br /><br /> のみ<br /><br /> (RO)|静的<br /><br /> (RO)|Keyset<br /><br /> ドリブン<br /><br /> (RO)|  
|--------------------------------------|-------------------------------------------|--------------------------------------------|-----------------------|----------------------------------|  
|DBPROP_SERVERCURSOR|F|T|T|T|  
|DBPROP_DEFERRED|F|F|-|-|  
|DBPROP_IrowsetChange|F|F|F|F|  
|DBPROP_IrowsetLocate|F|F|-|-|  
|DBPROP_IrowsetScroll|F|F|-|-|  
|DBPROP_IrowsetUpdate|F|F|F|F|  
|DBPROP_BOOKMARKS|F|F|-|-|  
|DBPROP_CANFETCHBACKWARDS|F|F|-|-|  
|DBPROP_CANSRCOLLBACKWARDS|F|F|-|-|  
|DBPROP_CANHOLDROWS|F|F|-|-|  
|DBPROP_LITERALBOOKMARKS|F|F|-|-|  
|DBPROP_OTHERINSERT|F|T|F|F|  
|DBPROP_OTHERUPDATEDELETE|F|T|F|T|  
|DBPROP_OWNINSERT|F|T|F|T|  
|DBPROP_OWNUPDATEDELETE|F|T|F|T|  
|DBPROP_QUICKSTART|F|F|-|-|  
|DBPROP_REMOVEDELETED|F|F|F|-|  
|DBPROP_IrowsetResynch|F|F|F|-|  
|DBPROP_CHANGEINSERTEDROWS|F|F|F|F|  
|DBPROP_SERVERDATAONINSERT|F|F|F|-|  
|DBPROP_UNIQUEROWS|-|F|F|F|  
|DBPROP_IMMOBILEROWS|-|-|-|T|  
  
|行セット プロパティ/カーソル モデル|動的 (RO)|キー セット (R/W)|動的 (R/W)|  
|--------------------------------------|--------------------|---------------------|----------------------|  
|DBPROP_SERVERCURSOR|T|T|T|  
|DBPROP_DEFERRED|-|-|-|  
|DBPROP_IrowsetChange|F|-|-|  
|DBPROP_IrowsetLocate|F|-|F|  
|DBPROP_IrowsetScroll|F|-|F|  
|DBPROP_IrowsetUpdate|F|-|-|  
|DBPROP_BOOKMARKS|F|-|F|  
|DBPROP_CANFETCHBACKWARDS|-|-|-|  
|DBPROP_CANSRCOLLBACKWARDS|-|-|-|  
|DBPROP_CANHOLDROWS|F|-|F|  
|DBPROP_LITERALBOOKMARKS|F|-|F|  
|DBPROP_OTHERINSERT|T|F|T|  
|DBPROP_OTHERUPDATEDELETE|T|T|T|  
|DBPROP_OWNINSERT|T|T|T|  
|DBPROP_OWNUPDATEDELETE|T|T|T|  
|DBPROP_QUICKSTART|-|-|-|  
|DBPROP_REMOVEDELETED|T|-|T|  
|DBPROP_IrowsetResynch|-|-|-|  
|DBPROP_CHANGEINSERTEDROWS|F|-|F|  
|DBPROP_SERVERDATAONINSERT|F|-|F|  
|DBPROP_UNIQUEROWS|F|F|F|  
|DBPROP_IMMOBILEROWS|F|T|F|  
  
 行セット プロパティの特定のセットに対して選択されるカーソル モデルは、次のようにして決まります。  
  
 行セット プロパティの指定されたコレクションから、上の表に示したプロパティのサブセットを取得します。 これらのプロパティを、上に示した表の各行セット プロパティのフラグ値、必須 (T、F) またはオプション (-) に応じて、2 つのサブグループに分けます。 最初の表から始め、左から右に向かってカーソル モデルごとに、2 つのサブグループ内のプロパティの値を、その列の対応するプロパティの値と比較します。 必須プロパティに不一致がなく、かつオプション プロパティの不一致が最も少ないカーソル モデルが選択されます。 複数のカーソル モデルが該当する場合は、一番左側のモデルが選択されます。  
  
## <a name="sql-server-cursor-block-size"></a>SQL Server カーソル ブロックのサイズ  
 ときに、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソルは、SQL Server の行セットの OLE DB ドライバーをサポートしている、行要素の数の配列パラメーターの処理、 **irowset::getnextrows**または**irowsetlocate::getrowsat**メソッドは、カーソル ブロックのサイズを定義します。 配列内のハンドルで指定される行が、カーソル ブロックのメンバーです。  
  
 ブックマークをサポートする、行の行ハンドルの取得を使用して、 **:getrowsbybookmark**メソッドは、カーソル ブロックのメンバーを定義します。  
  
 行セットの作成や [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソル ブロックの形成にどのメソッドを使用したかにかかわらず、行セットの次の行をフェッチするメソッドが実行されるまで、カーソル ブロックはアクティブです。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
