---
title: DataControl がエラー コード |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], DataControl
- DataControl errors [ADO]
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7996fb4bdda4e89ccdeb594a01d1a04732fb19e2
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="datacontrol-object-error-codes"></a>DataControl オブジェクトのエラー コード
次の表、 [.rds ですDataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)オブジェクトのエラー コード。 下位 2 バイトの正の 10 進変換、完全なエラー コードと 16 進数の値の負の値の 10 進数の翻訳が表示されます。

|RDS.DataControl がエラー コード|数値|Description|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107 -2146824175 0x800A1011|非同期操作が保留中の操作を実行できません。|
|**IDS_BadInlineTablegram**|4105 -2146824183 0x800A1009|不適切なインライン tablegram です。|
|**IDS_CantConnect**|4099 -2146824189 0x800A1003|サーバーに接続できません。|
|**IDS_CantCreateObject**|4100 -2146824188 0x800A1004|ビジネス オブジェクトを作成できません。|
|**IDS_CantFindDataspace**|4102 -2146824186 0x800A1006|データ領域のプロパティが正しくありません。|
|**IDS_CantInvokeMethod**|4101 -2146824187 0x800A1005|メソッドは、ビジネス オブジェクトで呼び出すことができません。|
|**IDS_CrossDomainWarning**|4112 -2146824170 0x800A1016|このページでは、別のドメイン上のデータにアクセスします。 これを許可しますか。 Internet Explorer では、このメッセージを避けるためには、ことができます、セキュリティで保護された Web サイトを追加する、信頼済みサイト ゾーンで、**セキュリティ**のタブ、**インターネット オプション** ダイアログ ボックス。|
|**IDS_InvalidADCClientVersion**|4106 -2146824176 0x800A1010|RDS クライアントのバージョンが無効です: クライアントがサーバーよりも新しいです。|
|**IDS_INVALIDARG**|5376 -2147019520 0x80071500|1 つ以上の引数が無効です。|
|**IDS_InvalidBindings**|4097 -2146824191 0x800A1001|プロパティのバインド エラー。|
|**IDS_InvalidParam**|4110 -2146824172 0x800A1014|1 つ以上の引数が無効です。|
|**IDS_NOINTERFACE**|5377 -2147019519 0x80071501|このようなインターフェイスがサポートされていません。|
|**IDS_NotReentrant**|4111 -2146824171 0x800A1015|イベント ハンドラーがまだ処理中に、要求を実行できません。|
|**IDS_ObjectNotSafe**|4103 -2146824185 0x800A1007|このコンピューターの安全性の設定には、ビジネス オブジェクトの作成が禁止されています。|
|**IDS_RecordsetNotOpen**|4109 -2146824173 0x800A1013|**レコード セット**が開かれていません。|
|**IDS_ResetInvalidField**|4108 -2146824174 0x800A1012|列に指定された**SortColumn**または**FilterColumn**存在しません。|
|**IDS_RowsetNotUpdateable**|4104 -2146824184 0x800A1008|行セットは更新できません。|
|**IDS_UnexpectedError**|4351 -2146823937 0x800A10FF|予期しないエラーがあります。|
|**IDS_UpdatesFailed**|4098 -2146824190 0x800A1002|データベースを更新できません。|
|**IDS_URLMONNotFound**|4119 -2146824169 0x800A1017|DataControl **URL**プロパティには、システム ファイルが見つかりません Urlmon.dll が必要です。|

## <a name="see-also"></a>参照
 [DataControl オブジェクト (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)
