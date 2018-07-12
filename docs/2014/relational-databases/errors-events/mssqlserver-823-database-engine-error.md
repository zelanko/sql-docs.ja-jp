---
title: MSSQLSERVER_823 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
caps.latest.revision: 24
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9945eb9eb980a1d103bda8f43c44f77fe6d7446e
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411911"
---
# <a name="mssqlserver823"></a>MSSQLSERVER_823
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|823|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|B_HARDERR|  
|メッセージ テキスト|オペレーティング システムにより、ファイル '%ls' のオフセット %#016I64x で %S_MSG 中の SQL Server にエラー %ls が返されました。 SQL Server エラー ログとシステム イベント ログ内の別のメッセージで詳細情報が報告されることもあります。 このシステムレベルのエラー状態は深刻で、データベースの一貫性を損なう可能性があるので、すぐに解決する必要があります。 完全なデータベース整合性確認 (DBCC CHECKDB) を完了させてください。 このエラーには多くの要因があります。詳細については、SQL Server オンライン ブックを参照してください。|  
  
## <a name="explanation"></a>説明  
 Windows の読み取り要求または書き込み要求が失敗しました。 Windows から返されたエラー コードと、対応するテキストがメッセージに挿入されます。 読み取り要求の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み取り要求の再試行が既に 4 回行われています。 このエラーは、ハードウェア エラーの結果として生じることが多く、デバイス ドライバーが原因になる場合もあります。 エラー 823 の詳細については、[http://support.microsoft.com/kb/828339](http://support.microsoft.com/kb/828339) を参照してください。 I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?LinkId=69370)」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 システム イベント ログで詳しい情報を調べます。 原因と対策については、ハードウェアの製造元またはマイクロソフト カスタマー サポート サービスまでお問い合わせください。 ハードウェア エラーの修正後、データベースをすべて復元し、DBCC CHECKDB を実行します。  
  
  
