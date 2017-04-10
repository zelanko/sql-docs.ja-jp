---
title: "パフォーマンス カウンター | Microsoft Docs"
ms.custom: ""
ms.date: "08/27/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ログ [Integration Services], パフォーマンス カウンター"
  - "パフォーマンス カウンター [Integration Services]"
  - "データ フロー [Integration Services], パフォーマンス"
  - "カウンター [Integration Services]"
  - "データ フロー エンジン [Integration Services]"
ms.assetid: 11e17f4e-72ed-44d7-a71d-a68937a78e4c
caps.latest.revision: 63
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 63
---
# パフォーマンス カウンター
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] により、データ フロー エンジンのパフォーマンスを監視するために使用できるパフォーマンス カウンターのセットがインストールされます。 たとえば、"Buffers spooled" カウンターを調べると、パッケージの実行中にデータ バッファーがディスクに一時的に書き込まれているかどうかを判断できます。 このスワップは、パフォーマンスを低下させると共に、コンピューターのメモリが不足していることを示しています。  
  
> **注:** [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] を実行するコンピューターに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] をインストールした後、コンピューターを [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] にアップグレードすると、アップグレード プロセスにより [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパフォーマンス カウンターがコンピューターから削除されます。 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のパフォーマンス カウンターをコンピューターに復元するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップを修復モードで実行してください。  
  
 次の表では、パフォーマンス カウンターについて説明します。  
  
|パフォーマンス カウンター|Description|  
|-------------------------|-----------------|  
|BLOB bytes read|データ フロー エンジンがすべてのソースから読み取ったバイナリ ラージ オブジェクト (BLOB) データのバイト数。|  
|BLOB bytes written|データ フロー エンジンがすべての出力先に書き込んだ BLOB データのバイト数。|  
|BLOB files in use|データ フロー エンジンがスプールのために現在使用している BLOB ファイル数。|  
|Buffer memory|使用中のメモリの量。 この数値には物理メモリと仮想メモリの両方が含まれている可能性があります。 数値が物理メモリ容量より大きい場合、メモリ スワップが増加していることを表す **Buffers Spooled** の数も増加します。 メモリ スワップが増加すると、データ フロー エンジンのパフォーマンスが低下します。|  
|Buffers in use|すべてのデータ フロー コンポーネントおよびデータ フロー エンジンが現在使用している、すべての種類のバッファー オブジェクト数。|  
|Buffers spooled|ディスクに現在書き込まれているバッファー数。 データ フロー エンジンが使用する物理メモリが不足している場合、現在使用されていないバッファーはディスクに書き込まれ、必要になった時点で再読み込みされます。|  
|Flat buffer memory|すべてのフラット バッファーが使用するメモリ総量 (バイト単位)。 フラット バッファーはコンポーネントがデータの格納に使用するメモリ ブロックです。 フラット バッファーはバイト単位でアクセスできる大きなブロックです。|  
|Flat buffers in use|データ フロー エンジンが使用するフラット バッファー数。 フラット バッファーはすべてプライベート バッファーです。|  
|Private buffer memory|すべてのプライベート バッファーが使用しているメモリ総量。 データ フロー エンジンがデータ フローをサポートするために作成した場合、バッファーはプライベートではありません。 プライベート バッファーは、変換が一時作業のためだけに使用するバッファーです。 たとえば、集計変換は作業のためにプライベート バッファーを使用します。|  
|Private buffers in use|変換が使用するバッファー数。|  
|Rows read|ソースが生成した行数。 この数値には、参照変換が参照テーブルから読み込む行は含まれません。|  
|Rows written|出力先に出力された行数。 この数値には、出力先データ ストアに書き込まれた行は含まれません。|  
  
 Microsoft 管理コンソール (MMC) のパフォーマンス スナップインを使用して、パフォーマンス カウンターの値を取得するログを作成します。  
  
 パフォーマンスを向上させる方法については、「[データ フロー パフォーマンス機能](../../integration-services/data-flow/data-flow-performance-features.md)」を参照してください。  
  
## パフォーマンス カウンター統計の取得  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーに配置された [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトについて、[dm_execution_performance_counters (SSISDB データベース)](../Topic/dm_execution_performance_counters%20\(SSISDB%20Database\).md) 関数を使用してパフォーマンス カウンター統計を取得できます。  
  
 次の例では、ID が 34 である処理中の実行の統計を関数で返します。  
  
```  
select * from [catalog].[dm_execution_performance_counters] (34)  
```  
  
 次の例では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーで処理中のすべての実行の統計を関数で返します。  
  
```  
select * from [catalog].[dm_execution_performance_counters] (NULL)  
  
```  
  
> **重要!!** メンバーである場合、**ssis_admin** データベース ロール、実行中のすべての実行のパフォーマンス統計が返されます。  メンバーでない場合、**ssis_admin** データベース ロール、実行中に、アクセス許可を参照する実行のパフォーマンス統計が返されます。  
  
## 関連コンテンツ  
  
-   codeplex.com のツール ([Business Intelligence Development Studio のための SSIS パフォーマンス ビジュアライゼーション (CodePlex Project)](http://go.microsoft.com/fwlink/?LinkId=146626))  
  
-   msdn.microsoft.com のビデオ ([社内の SSIS パッケージのパフォーマンスの測定と理解 (SQL Server ビデオ)](http://go.microsoft.com/fwlink/?LinkId=150497))  
  
-   support.microsoft.com のサポート技術情報 ([Windows Server 2008 へのアップグレード後にパフォーマンス モニターで SSIS パフォーマンス カウンターが使用できなくなる](http://go.microsoft.com/fwlink/?LinkId=235319))  
  
## 参照  
 [プロジェクトとパッケージの実行](https://msdn.microsoft.com/library/ms141708.aspx)  
  
  