---
title: CreateRecordset メソッド (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords:
- CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a8646fba41809fe3ed6a062e7a066ed0dce5c007
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63298914"
---
# <a name="createrecordset-method-rds"></a>CreateRecordset メソッド (RDS)
空を作成します。 切断[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)します。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 以降、RDS サーバー コンポーネントに含まれていない、Windows オペレーティング システム (Windows 8 を参照してくださいと[Windows Server 2012 の互換性クックブック](https://www.microsoft.com/download/details.aspx?id=27416)の詳細)。 RDS クライアント コンポーネントは、Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *Object*  
 オブジェクト変数を表す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)または[rds.DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *ColumnsInfos*  
 A**バリアント**内の各列を定義する属性の配列、 **Recordset**を作成します。 各列の定義には、次の 4 つの必須の属性と 1 つの省略可能な属性の配列が含まれています。  
  
|属性|説明|  
|---------------|-----------------|  
|名前|列ヘッダーの名前。|  
|型|データ型の整数。|  
|サイズ|データ型に関係なく、文字幅の整数。|  
|NULL 値の許容|ブール値。|  
|(省略可能) のスケール|この省略可能な属性は、数値フィールドの小数点以下桁数を定義します。 この値が指定されていない場合は 3 つの小数点以下桁数に数値の値は切り捨てられます。 有効桁数が影響を受けませんが、小数点以下桁数は 3 つに切り捨てられます。|  
  
 列の配列のセットが定義する配列にグループ化し、 **Recordset**します。  
  
## <a name="remarks"></a>コメント  
 サーバー側ビジネス オブジェクトが、その結果を設定することができます**レコード セット**、OLE DB 以外のデータ プロバイダーからデータをなど、オペレーティング システム ファイル株価情報を格納します。  
  
 次の表、[格納](../../../ado/reference/ado-api/datatypeenum.md)によってサポートされる値、 **CreateRecordset**メソッド。 の順には、参照番号フィールドを定義するために使用します。  
  
 各データ型は、固定長または可変長。 サイズは、事前に定義されたサイズの定義がまだ必要なために、サイズが-1 の固定長型を定義する必要があります。 可変長データ型は、1 から 32767 までのサイズを許可します。  
  
 変数のデータ型の一部で、型が強制的に代替列に記載されていることができます。 後までの代替文字列が表示されませんが、 **Recordset**を作成して入力します。 必要に応じて、実際のデータ型の確認できます。  
  
|長さ|定数|数値|Substitution|  
|------------|--------------|------------|------------------|  
|固定|**adTinyInt**|16||  
|固定|**adSmallInt**|2||  
|固定|**adInteger**|3||  
|固定|**adBigInt**|20||  
|固定|**adUnsignedTinyInt**|17||  
|固定|**adUnsignedSmallInt**|18||  
|固定|**adUnsignedInt**|19||  
|固定|**adUnsignedBigInt**|21||  
|固定|**adSingle**|4||  
|固定|**adDouble**|5||  
|固定|**adCurrency**|6||  
|固定|**adDecimal**|14||  
|固定|**adNumeric**|131||  
|固定|**adBoolean**|11||  
|固定|**adError**|10||  
|固定|**adGuid**|72||  
|固定|**adDate**|7||  
|固定|**adDBDate**|133||  
|固定|**adDBTime**|134||  
|固定|**adDBTimestamp**|135|7|  
|変数|**adBSTR**|8|130|  
|変数|**adChar**|129|200|  
|変数|**adVarChar**|200||  
|変数|**adLongVarChar**|201|200|  
|変数|**adWChar**|130||  
|変数|**adVarWChar**|202|130|  
|変数|**adLongVarWChar**|203|130|  
|変数|**adBinary**|128||  
|変数|**adVarBinary**|204||  
|変数|**adLongVarBinary**|205|204|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataFactory オブジェクト (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)|  
  
## <a name="see-also"></a>参照  
 [CreateRecordset メソッドの例 (VB)](../../../ado/reference/ado-api/createrecordset-method-example-vb.md)   
 [CreateRecordset メソッドの例 (VBScript)](../../../ado/reference/rds-api/createrecordset-method-example-vbscript.md)   
 [CreateObject メソッド (RDS)](../../../ado/reference/rds-api/createobject-method-rds.md)



