---
title: CommandTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CommandTypeEnum
helpviewer_keywords:
- CommandTypeEnum enumeration [ADO]
ms.assetid: 4b1feb9c-a855-40fe-a906-efe688687e9f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5a2de155d9c4a61246245b2c7f9c3c73a535994a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67919682"
---
# <a name="commandtypeenum"></a>CommandTypeEnum
コマンド引数をどのように解釈するかを指定します。  
  
 ユーザーが指定した*Commandstring*値を検証して、ADO にとって危険な可能性のあるコマンドを挿入する機会をアプリケーションユーザーに与えないようにすることが重要です。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adCmdUnspecified**|-1|は、コマンドの型引数を指定していません。|  
|**Adodb.commandtypeenum.adcmdtext**|1 で保護されたプロセスとして起動されました|[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)をコマンドまたはストアドプロシージャの呼び出しのテキスト定義として評価します。|  
|**adCmdTable**|2|**CommandText**を、内部で生成された SQL クエリによって返される列を持つテーブル名として評価します。|  
|**adCmdStoredProc**|4|**CommandText**をストアドプロシージャ名として評価します。|  
|**adCmdUnknown**|8|既定。 **CommandText**プロパティ内のコマンドの型が不明であることを示します。<br /><br /> コマンドの種類が不明な場合、ADO は**CommandText**をいくつかの方法で解釈しようとします。<br /><br /> -   **CommandText**は、コマンドまたはストアドプロシージャの呼び出しのテキスト定義として解釈されます。 これは、 **Adcmdtext**と同じ動作です。<br />-   **CommandText**は、ストアドプロシージャの名前を指定します。 これは**adCmdStoredProc**と同じ動作です。<br />-   **CommandText**は、テーブルの名前として解釈されます。 すべての列は、内部で生成された SQL クエリによって返されます。 これは、 **Adcmdtable**と同じ動作です。|  
|**adCmdFile**|256|は、永続的に格納された[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)のファイル名として**CommandText**を評価します。 レコードセットで使用され**ます。**[Open](../../../ado/reference/ado-api/open-method-ado-recordset.md)または[Requery](../../../ado/reference/ado-api/requery-method.md)のみ。|  
|**adCmdTableDirect**|512|すべての列が返されたテーブル名として**CommandText**を評価します。 レコードセットで使用され**ます。 Open**または**Requery**のみです。 [Seek](../../../ado/reference/ado-api/seek-method.md)メソッドを使用するには、**レコードセット**を**adcmdtabledirect**で開く必要があります。<br /><br /> この値を[Executeoptionenum](../../../ado/reference/ado-api/executeoptionenum.md)値**adasyncexecute**と組み合わせることはできません。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums STOREDPROC|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums. TABLEDIRECT|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[CommandType プロパティ (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)|[Execute メソッド (ADO Command)](../../../ado/reference/ado-api/execute-method-ado-command.md)|  
|[Execute メソッド (ADO Connection)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|[Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|  
|[Requery メソッド](../../../ado/reference/ado-api/requery-method.md)||
