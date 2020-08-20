---
description: MSSQLSERVER_833
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02e7e0bbca8e81cc39da4c15a096ee0600138db3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88499521"
---
# <a name="mssqlserver_833"></a>MSSQLSERVER_833
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|833|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|BUF_LONG_IO|  
|メッセージ テキスト|SQL Server は、データベース `[%ls] (%d)` のファイル [%ls] で、完了に %d 秒以上かかった I/O 要求を %d 個検出しました。  OS ファイル ハンドルは 0x%p です。  最新の実行時間の長い I/O のオフセットは %#016I64x です。|  
  
## <a name="explanation"></a>説明  
このメッセージは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がディスクからの読み取り要求やディスクへの書き込み要求を発行してからその要求が完了するまでの時間が 15 秒を超えたことを示しています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からこのエラーが報告された場合は、I/O サブシステムに問題があります。 また、このメッセージに関連して次のような他の現象が発生する可能性があります: PAGEIOLATCH の長い待機時間、システム イベント ログの警告またはエラー、システム モニター カウンターでのディスク待機時間の問題の兆候。 
  
### <a name="possible-causes"></a>考えられる原因  
この問題の原因としては、オペレーティング システムのパフォーマンスの問題、ハードウェア エラー、ファームウェア エラー、デバイス ドライバーの問題、I/O プロセスまたはデータベース ファイルのストレージ パスでのフィルター ドライバーの介入などが考えられます。 SQL Server により、I/O 要求が開始された時刻と、I/O が完了した時刻が記録されます。 その差が 15 秒以上の場合、この状態が検出されます。 これは、このメッセージによって説明および報告される I/O 遅延状態の原因が、SQL Server ではないことも意味します。 この状態は、一般に "停止した I/O" と呼ばれます。 ほとんどのディスク要求は、ディスクの標準的な速度で行われます。 この標準的なディスク速度は、"ディスク シーク時間" と呼ばれることがよくあります。 ほとんどの標準的なディスクのディスク シーク時間は 10 ミリ秒以下になります。 したがって、システム I/O パスが SQL Server に戻るのに 15 秒かかるのは、非常に長い時間です。 
  
## <a name="user-action"></a>ユーザーの操作  
このエラーのトラブルシューティングを行うには、システム イベント ログを参照し、ハードウェア関連のエラー メッセージが記録されているかどうかを調べます。 また、可能な場合はハードウェア固有のログも調べます。 必要な方法と手法を使用して、オペレーティング システム、ドライバー、または I/O ハードウェアにおける遅延の原因を特定する必要があります。 この問題を解決するには、すべてのデバイス ドライバーとファームウェアを更新したり、ディスク システムに関連する他の診断を実行したりすることがあります。 
  
パフォーマンス モニターを使用して、次のカウンターを調べます。  
  
-   **Average Disk Sec/Transfer**  
  
-   **Average Disk Queue Length**  
  
-   **Current Disk Queue Length**  
  
たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を実行しているコンピューターの **Average Disk Sec/Transfer** の時間は、通常 15 ミリ秒未満です。 **Avg. Disk sec/Transfer** の値が増加している場合、I/O サブシステムが I/O 要求を最適な速度で処理できていません。

また、[Storport ETW ログ](https://docs.microsoft.com/archive/blogs/ntdebugging/storport-etw-logging-to-measure-requests-made-to-a-disk-unit)のような機能を使用して、ディスク ユニットに対して行われた要求の待機時間を測定することもできます。 [Windows Performance Recorder](https://docs.microsoft.com/windows-hardware/test/wpt/introduction-to-wpr) の組み込みプロファイルとして、他の同様のディスク I/O トラブルシューティング キットを使用できます。
  
> [!NOTE]  
> ディスク アクセス速度は、ウイルス対策プログラムによって低下する場合があります。 アクセスを高速化するには、エラー メッセージに示されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ファイルをアクティブ ウイルス スキャンの対象から除外します。 [fltmc.exe コマンド ライン ユーティリティ](https://docs.microsoft.com/windows-hardware/drivers/ifs/development-and-testing-tools#fltmcexe-control-program)を使用すると、システムにインストールされているすべてのフィルター ドライバーを照会し、データベース ファイルへのストレージ パスに対して実行される機能を把握できます。 
  
I/O エラーの詳細については、「[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))」と、[https://support.microsoft.com/kb/897284/en-us](https://support.microsoft.com/kb/897284/en-us) にあるサポート技術情報の資料を参照してください。  
  
