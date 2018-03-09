---
title: MSSQLSERVER_824 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1081907bbb680dc5eb2ec2a2fa171f9e879a9a46
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver824"></a>MSSQLSERVER_824
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|824|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|B_HARDSSERR|  
|メッセージ テキスト|SQL Server で、一貫性に基づいた論理 I/O エラーが検出されました: %ls。 このエラーは、ファイル '%ls' のオフセット %#016I64x にあるデータベース ID が %d のページ %S_PGID の %S_MSG 中に発生しました。  SQL Server エラー ログまたはシステム イベント ログ内の別のメッセージで詳細情報が報告されることもあります。|  
  
## <a name="explanation"></a>説明  
このエラーは、ディスクからページが正常に読み取られたことが Windows によって報告されたが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によってそのページに異常が検出されたことを示しています。 このエラーは、Windows によってエラーが検出されなかった点を除けば、エラー 823 と似ています。 通常は、ディスク ドライブの欠陥、ディスクのファームウェアの問題、デバイス ドライバーの障害など、I/O サブシステムに問題があることを示しています。 I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](http://go.microsoft.com/fwlink/?LinkId=69370)」 (Microsoft SQL Server I/O の基礎 (第 2 章)) を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
  
### <a name="look-for-hardware-failure"></a>ハードウェア障害を調査する  
ハードウェアの診断を実行し、問題があれば修正します。 また、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のシステム ログとアプリケーション ログ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログを参照して、ハードウェア障害の結果としてエラーが発生しているかどうかを確認します。 ログに記録されているハードウェアに関する問題があれば、それを修正します。  
  
データ破損の問題が解決しない場合は、ハードウェア コンポーネントを他のものと交換し、問題の原因を特定するようにしてください。 システムで、ディスク コントローラーの書き込みキャッシュが有効になっていないことを確認します。 書き込みキャッシュが問題と思われる場合は、ハードウェア ベンダーにお問い合わせください。  
  
それでも問題が解決しない場合は、新しいハードウェア システムの導入をご検討ください。 導入の際には、ディスク ドライブの再フォーマットとオペレーティング システムの再インストールが必要になる場合があります。  
  
### <a name="restore-from-backup"></a>バックアップから復元する  
問題がハードウェアに関するものではなく、また既知のクリーン バックアップがある場合は、そのバックアップを使用してデータベースを復元します。  
  
PAGE_VERIFY CHECKSUM オプションを使用するようにデータベースを変更することを検討します。 PAGE_VERIFY の詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](~/t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
[suspect_pages テーブルの管理 &#40;SQL Server&#41;](~/relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
