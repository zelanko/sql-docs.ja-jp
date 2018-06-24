---
title: MSSQLSERVER_26014 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 26014 (Database Engine error)
ms.assetid: e2b0dfc7-0681-4e5d-8875-1d5f63534086
caps.latest.revision: 10
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 39245a47417ea81a0454e82ac7f76b2d6cd9e6f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074611"
---
# <a name="mssqlserver26014"></a>MSSQLSERVER_26014
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|26014|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SNI_SSL_USER_CERT_FAILURE|  
|メッセージ テキスト|ユーザーが指定した証明書 [Cert Hash(sha1) "%hs"] を読み込むことができません。 サーバー側では接続が許可されません。 証明書が正しくインストールされていることを確認してください。 オンライン ブックの「SSL に使用する証明書の構成」を参照してください。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、メッセージで指定された証明書を読み込もうとしましたが、読み込み操作に失敗しました。 この証明書を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用するには、この問題を解決する必要があります。  
  
 エラーの原因として以下が考えられます。  
  
-   証明書が移動または削除されている可能性があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用するログインを変更した場合は、証明書にアクセスする権限が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にない可能性があります。  
  
-   証明書の有効期限が切れている可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 メッセージで指定された証明書がシステム上に存在すること、その証明書にアクセスできること、およびその証明書が使用可能であることを確認します。  
  
  