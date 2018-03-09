---
title: "Microsoft OLE DB 永続化プロバイダー (ADO サービス プロバイダー) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30df806429167550cdf39f064e349e46dd692502
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Microsoft OLE DB の永続化プロバイダーの概要
Microsoft OLE DB 永続化プロバイダーでは、保存することができます、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)をファイルにオブジェクトを後で復元が**レコード セット**ファイルからのオブジェクト。 スキーマ情報、データ、および保留中の変更は保持されます。

 保存することができます、 **Recordset**専用の高度なデータ テーブル グラム (adtg 形式) 形式またはオープン拡張マークアップ言語 (XML) 形式のいずれかにします。

## <a name="provider-keyword"></a>プロバイダーのキーワード
 このプロバイダーを起動するには、接続文字列で、次のキーワードと値を指定します。

```
"Provider=MSPersist"
```

## <a name="errors"></a>エラー
 アプリケーションでは、このプロバイダーによって発行された、次のエラーを検出できます。

|定数|Description|
|--------------|-----------------|
|E_BADSTREAM|開かれたファイルが有効な形式ではありません (つまり、形式が adtg 形式または XML) です。|
|E_CANTPERSISTROWSET|**Recordset**保存されているオブジェクトは特徴格納されるを防ぐことがあります。|

## <a name="remarks"></a>解説
 動的なプロパティを公開している Microsoft OLE DB 永続化プロバイダーはありません。

 現時点では、のみパラメーター化された階層**Recordset**オブジェクトを保存できません。

 永続的に保存の詳細については**Recordset** 、オブジェクトを参照してください[レコード セットの永続化](../../../ado/guide/data/more-about-recordset-persistence.md)です。

 開くには、ストリームを使用する場合、 **Recordset、**以外の指定されたパラメーターことはありません、*ソース*のパラメーター、**開く**メソッドです。

## <a name="see-also"></a>参照
[Microsoft OLE DB 永続化プロバイダー (ADO サービス プロバイダー)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
