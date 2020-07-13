---
title: DCOM ストリームマーシャリング形式を設定する |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- dcom stream marshaling format in rds [ADO]
ms.assetid: 46664ac5-d6e6-4457-8bae-3a98300f2a41
author: rothja
ms.author: jroth
ms.openlocfilehash: f3e7dd82d54b20ccceec73c0917f4f81c3cf16dd
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2020
ms.locfileid: "82758958"
---
# <a name="setting-dcom-stream-marshaling-format"></a>DCOM のストリームのマーシャリング形式の設定
Rds 1.5 以前のコンポーネントを使用するクライアントコンピューターは、RDS 2.0 以降のコンポーネントを使用するサーバーと互換性がありません。 基盤となるプロトコルとして DCOM を使用する場合は、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクトを転送する際に RDS 2.0 以降のサポートがより効率的になります。 クライアントが RDS 1.5 以前のコンポーネントを実行している場合は、以前の RDS サポート (RDS 1.0 と呼ばれます) または新しい RDS サポート (RDS 2.0 以降と呼ばれます) を使用するようにサーバーを設定できます。 次のレジストリエントリのいずれかを設定します。  
  
> [!IMPORTANT]
>  Windows 8 と windows Server 2012 以降では、RDS サーバーコンポーネントが Windows オペレーティングシステムに含まれなくなりました (詳細については、「Windows 8 および[Windows server 2012 の互換性に関するクックブック](https://www.microsoft.com/download/details.aspx?id=27416)」を参照してください)。 RDS クライアントコンポーネントは、今後のバージョンの Windows では削除される予定です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションは、 [WCF Data Service](https://go.microsoft.com/fwlink/?LinkId=199565)に移行する必要があります。  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS10"  
```  
  
 \- または -  
  
```console
[HKEY_CLASSES_ROOT]  
\CLSID\[58ECEE30-E715-11CF-B0E3-00AA003F000F}\ADTGOptions]"MarshalFormat"="RDS20"  
```


