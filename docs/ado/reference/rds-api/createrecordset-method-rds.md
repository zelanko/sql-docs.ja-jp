---
title: "CreateRecordset メソッド (RDS) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- DataControl::CreateRecordset
- RDS.DataControl::CreateRecordset
- CreateRecordset
- RDSServer.DataFactory::CreateRecordset
- DataFactory::CreateRecordset
helpviewer_keywords: CreateRecordset method [RDS]
ms.assetid: 6840b1e5-c04d-4d3e-9dcc-42128c83492f
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2a1bec5dc5b8c0e159755c9689aac0c9bfc40217
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="createrecordset-method-rds"></a>CreateRecordset メソッド (RDS)
空、作成切断[Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)です。  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.CreateRecordset(ColumnInfos)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *オブジェクト*  
 オブジェクト変数を表す、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)または[.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクト。  
  
 *ColumnsInfos*  
 A**バリアント**内の各列を定義する属性の配列、 **Recordset**を作成します。 各列の定義には、次の 4 つの必須の属性と 1 つの省略可能な属性の配列が含まれています。  
  
|属性|Description|  
|---------------|-----------------|  
|名前|列ヘッダーの名前。|  
|型|データ型の整数です。|  
|サイズ|データ型に関係なく、文字幅の整数です。|  
|NULL 値の許容|ブール値です。|  
|(省略可能) 小数点以下桁数|この省略可能な属性では、数値フィールドの小数点以下桁数を定義します。 この値が指定されていない場合は 3 つのスケールに数値は切り捨てられます。 有効桁数が影響を受けませんが、小数点以下桁数は 3 桁に切り捨てられます。|  
  
 列の配列のセットが、配列を定義するにグループ化し、 **Recordset**です。  
  
## <a name="remarks"></a>解説  
 サーバー側のビジネス オブジェクトは、その結果を設定できる**レコード セット**以外の OLE DB データ プロバイダーからデータをなど、オペレーティング システム ファイルを含む株価情報。  
  
 次の表、[格納](../../../ado/reference/ado-api/datatypeenum.md)によってサポートされる値、 **CreateRecordset**メソッドです。 の順には、フィールドを定義するために使用する参照番号です。  
  
 データ型は固定長または可変長のどちらかです。 サイズは、あらかじめ決められた、サイズの定義が必要であるために、サイズが – 1 の固定長の型を定義してください。 可変長データ型は、1 から 32767 までのサイズを許可します。  
  
 変数のデータ型の一部で、型が強制的に置換列に記載されていることができます。 後まで代替文字列は表示されません、 **Recordset**を作成して入力します。 必要に応じて、実際のデータ型を確認できます。  
  
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
|変数|**ファミリ**|129|200|  
|変数|**異なる**|200||  
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



