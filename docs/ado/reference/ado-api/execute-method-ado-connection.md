---
title: Execute メソッド (ADO 接続) |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::Execute
- Connection15::raw_Execute
helpviewer_keywords:
- Execute method [ADO]
ms.assetid: 03c69320-96b2-4d85-8d49-a13b13e31578
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 27f99015571bd7abdad402dc0f779c04fd546a79
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="execute-method-ado-connection"></a>Execute メソッド (ADO 接続)
指定されたクエリ、SQL ステートメント、ストアド プロシージャ、またはプロバイダー固有のテキストを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
Set recordset = connection.Execute (CommandText, RecordsAffected, Options)  
```  
  
## <a name="return-value"></a>戻り値  
 返します、[レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト参照。  
  
#### <a name="parameters"></a>パラメーター  
 *CommandText*  
 A**文字列**値を含む SQL ステートメント、ストアド プロシージャ、URL、またはプロバイダー固有のテキストを実行します。 **必要に応じて**テーブル名は、プロバイダーが SQL 対応である場合のみ、使用できます。 「顧客」の場合は、テーブル名の例を使用すると、ADO は自動的に先頭に付加、標準的な SQL Select の構文形式し、「選択 * から顧客」を渡すとして、[!INCLUDE[tsql](../../../includes/tsql_md.md)]プロバイダーにステートメントです。  
  
 *RecordsAffected*  
 省略可。 A**長い**先変数プロバイダーが返されます、操作の影響を受けるレコードの数。  
  
 *Options*  
 省略可。 A**長い**をプロバイダーに、CommandText 引数を評価する方法を示す値。 1 つ以上のビットマスクを指定できます[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)または[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)値。  
  
 **注**を使用して、 **ExecuteOptionEnum**値**adExecuteNoRecords**内部処理を最小限に抑えることによって、および Visual Basic 6.0 から移植するアプリケーションのパフォーマンスを向上させるためにします。  
  
 使用しないでください**adExecuteStream**で、 **Execute**のメソッド、**接続**オブジェクト。  
  
 いない値を使用しないで、CommandTypeEnum adCmdFile または adCmdTableDirect の Execute を使用します。 これらの値は、オプションとしてのみ使用できます、 [Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)と[Requery メソッド](../../../ado/reference/ado-api/requery-method.md)のメソッド、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 使用して、 **Execute**メソッドを[接続オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)オブジェクトがどのようなクエリを指定した接続で CommandText 引数内のメソッドに渡すを実行します。 新規の実行によって生成される結果が格納された CommandText 引数は、行を返すクエリを指定する場合**Recordset**オブジェクト。 プロバイダーが返すかどうか、コマンドはありません (たとえば、SQL UPDATE クエリ) の結果を返す**Nothing**オプションとして長さ**adExecuteNoRecords**が指定されているそれ以外の場合を返しますを実行、。閉じられた**Recordset**です。  
  
 返された**Recordset**オブジェクトは読み取り専用、順方向専用カーソルでは常にします。 必要がある場合、**レコード セット**オブジェクトより多くの機能を最初に作成、**レコード セット**、目的のプロパティの設定を持つオブジェクトを使用して、 **Recordset**オブジェクト[Open メソッド (ADO レコード セット)](../../../ado/reference/ado-api/open-method-ado-recordset.md)クエリを実行して、目的のカーソルの種類を返すメソッド。  
  
 内容、 *CommandText*引数は、プロバイダーに固有であり標準の SQL 構文またはプロバイダーがサポートする固有のコマンド形式を指定できます。  
  
 この操作の終了時に ExecuteComplete イベントが発行されます。  
  
> [!NOTE]
>  Http スキームを使用する Url が自動的に起動、 [Microsoft OLE DB Provider for Internet Publishing](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)です。 詳細については、次を参照してください。[絶対と相対 Url](../../../ado/guide/data/absolute-and-relative-urls.md)です。  
  
## <a name="applies-to"></a>適用対象  
 [Connection オブジェクト (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)
