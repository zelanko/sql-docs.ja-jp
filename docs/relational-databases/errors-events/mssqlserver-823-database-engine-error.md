---
title: MSSQLSERVER - データベース エンジン エラー | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f17ce560ef7ee5917fb76b997636fb079327d8b7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68007032"
---
# <a name="mssqlserver---database-engine-error"></a>MSSQLSERVER - データベース エンジン エラー
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
Windows の読み取り要求または書き込み要求が失敗しました。 Windows から返されたエラー コードと、対応するテキストがメッセージに挿入されます。 読み取り要求の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって読み取り要求の再試行が既に 4 回行われています。 このエラーは、ハードウェア エラーの結果として生じることが多く、デバイス ドライバーが原因になる場合もあります。 エラー 823 の詳細については、[https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339) を参照してください。 I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
システム イベント ログで詳しい情報を調べます。 原因と対策については、ハードウェアの製造元またはマイクロソフト カスタマー サポート サービスまでお問い合わせください。 ハードウェア エラーの修正後、データベースをすべて復元し、DBCC CHECKDB を実行します。  
  
