---
title: Microsoft OLE DB 永続化プロバイダー (ADO サービスプロバイダー) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- providers [ADO], OLE DB persistence provider
- persistence provider [ADO]
- OLE DB persistence provider [ADO]
ms.assetid: e75ef0dc-2016-4fcc-8918-23311c0d4e02
author: rothja
ms.author: jroth
ms.openlocfilehash: cc8c8f099e703433f57e9d8ff463e229213503be
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758468"
---
# <a name="microsoft-ole-db-persistence-provider-overview"></a>Microsoft OLE DB 永続化プロバイダーの概要
Microsoft OLE DB 永続化プロバイダーを使用すると、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトをファイルに保存し、後でその**レコードセット**オブジェクトをファイルから復元できます。 スキーマ情報、データ、および保留中の変更は保持されます。

 この**レコードセット**は、独自の高度なデータテーブルグラム (ADTG) 形式または open 拡張マークアップ言語 (XML) 形式のいずれかで保存できます。

## <a name="provider-keyword"></a>Provider キーワード
 このプロバイダーを呼び出すには、接続文字列に次のキーワードと値を指定します。

```vb
"Provider=MSPersist"
```

## <a name="errors"></a>エラー
 このプロバイダーによって発行された次のエラーは、アプリケーションで検出できます。

|定数|説明|
|--------------|-----------------|
|E_BADSTREAM|開かれたファイルの形式が有効ではありません (つまり、形式が ADTG または XML ではありません)。|
|E_CANTPERSISTROWSET|保存された**レコードセット**オブジェクトには、保存されないようにする特性があります。|

## <a name="remarks"></a>解説
 Microsoft OLE DB 永続化プロバイダーは動的プロパティを公開しません。

 現時点では、パラメーター化された階層的な**レコードセット**オブジェクトのみを保存することはできません。

 **レコードセット**オブジェクトを永続的に格納する方法の詳細については、「[レコードセット永続](../../../ado/guide/data/more-about-recordset-persistence.md)化」を参照してください。

 ストリームを使用して**レコードセット**を開くときに、 **Open**メソッドの*Source*パラメーター以外にパラメーターを指定しないようにする必要があります。

## <a name="see-also"></a>参照
[Microsoft OLE DB 永続化プロバイダー (ADO サービスプロバイダー)](../../../ado/guide/appendixes/microsoft-ole-db-persistence-provider-ado-service-provider.md)
