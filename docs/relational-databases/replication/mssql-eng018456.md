---
title: MSSQL_ENG018456 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 8fce0bf03cae509c78756de602dfc3d79f983c59
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656336"
---
# <a name="mssqleng018456"></a>MSSQL_ENG018456
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|18456|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|ユーザー '%.*ls'.%.\*ls はログインできませんでした|  
  
## <a name="explanation"></a>説明  
 ログインの試行が失敗するたびに、エラー MSSQL_ENG018456 が発生します。 エラー メッセージにアカウント **distributor_admin** が含まれている場合 ("ユーザー 'distributor_admin' はログインできませんでした。" となっている場合)、問題はレプリケーションによって使用されているアカウントに関するものです。 レプリケーションによってリモート サーバー **repl_distributor**が作成され、これによってディストリビューターとパブリッシャーの間の通信が可能になります。 ログイン **distributor_admin** は、このリモート サーバーに関連付けられており、有効なパスワードを持つ必要があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 このアカウントに対するパスワードを指定したことを確認します。 詳細については、「[ディストリビューターのセキュリティ保護](../../relational-databases/replication/security/secure-the-distributor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
