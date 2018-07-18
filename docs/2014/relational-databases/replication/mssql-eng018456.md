---
title: MSSQL_ENG018456 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG018456 error
ms.assetid: 3daa8144-d81f-445a-b6c3-4bb3e9fd1526
caps.latest.revision: 14
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b09ff007bdd80839eac5f992bce17b16c5adaf8c
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37278848"
---
# <a name="mssqleng018456"></a>MSSQL_ENG018456
    
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
 このアカウントに対するパスワードを指定したことを確認します。 詳細については、「[ディストリビューターのセキュリティ保護](security/secure-the-distributor.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
