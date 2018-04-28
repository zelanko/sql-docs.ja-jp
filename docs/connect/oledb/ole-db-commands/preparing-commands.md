---
title: コマンドの準備 |Microsoft ドキュメント
description: SQL Server の OLE DB Driver を使用してコマンドを準備します。
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db-commands
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, commands
- prepared statements [OLE DB Driver for SQL Server]
- commands [OLE DB]
- command preparation [OLE DB Driver for SQL Server]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 420ef1abfdb17f40055220d1aa0453598aca156c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="preparing-commands"></a>コマンドの準備
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL Server の OLE DB Driver では、1 つのコマンドの複数の実行を最適化のコマンドの準備がサポートします。ただし、コマンドの準備は、オーバーヘッドを生成し、コンシューマーは、複数回実行するコマンドを準備する必要はありません。 一般的には、コマンドを 4 回以上実行する場合に準備します。  
  
 パフォーマンス上の理由から、コマンドの準備は、コマンドが実行されるまで遅延されます。 これは既定の動作です。 準備中のコマンドのエラーは、コマンドまたはメタプロパティ操作が実行されるまで認識されません。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の SSPROP_DEFERPREPARE プロパティを FALSE に設定すると、この既定の動作を無効にできます。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、コマンドを (最初に準備しないで) 直接実行すると、実行プランが作成され、キャッシュされます。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には新しいステートメントをキャッシュ内の既存の実行プランと照合する効率的なアルゴリズムがあるので、SQL ステートメントを再実行すると、そのステートメントの実行プランが再利用されます。  
  
 準備されたコマンドに対して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではコマンド ステートメントの準備と実行に関するネイティブ サポートが提供されます。 ステートメントを準備すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では実行プランが作成されてキャッシュされ、この実行プランのハンドルがプロバイダーに返されます。 その後、プロバイダーはこのハンドルを使用して、ステートメントを繰り返し実行します。 ストアド プロシージャは作成されません。 直接実行する場合のように SQL ステートメントをキャッシュ内の実行プランと照合するのではなく、ハンドルで SQL ステートメントの実行プランを直接識別するので、そのステートメントを複数回実行することがわかっている場合は、ステートメントを準備する方が直接実行するよりも効率的です。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、準備されたステートメントを一時オブジェクトの作成に使用できません。また、準備されたステートメントから、一時テーブルなどの一時オブジェクトを作成するシステム ストアド プロシージャを参照できません。 このようなプロシージャは、直接実行する必要があります。  
  
 コマンドによっては、準備してはいけないものがあります。 たとえば、ストアド プロシージャの実行を指定するコマンドや、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャの作成に関して無効なテキストを含むコマンドは、準備しないようにしてください。  
  
 一時ストアド プロシージャを作成する場合、OLE DB Driver for SQL Server は、ステートメント自体が実行された場合、結果を返す、一時ストアド プロシージャを実行します。  
  
 一時ストアド プロシージャの作成は、SQL Server の OLE DB ドライバーによって制御されます、特定の初期化プロパティ SSPROP_INIT_USEPROCFORPREP です。 プロパティ値が SSPROPVAL_USEPROCFORPREP_ON または SSPROPVAL_USEPROCFORPREP_ON_DROP の場合は、SQL Server の OLE DB Driver は、コマンドを準備するときに、ストアド プロシージャを作成しようとします。 ストアド プロシージャの作成は、アプリケーション ユーザーが適切な [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 権限を所持している場合に成功します。  
  
 一時ストアド プロシージャの作成、ほとんど切断しないコンシューマーの大量のリソースを要求できます**tempdb**、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]システム データベースの一時オブジェクトが作成されます。 コマンドを作成したセッションがのインスタンスへの接続を失ったときにのみ、SQLServerのOLEDBドライバーによって作成される一時ストアドプロシージャが削除されるSSPROP_INIT_USEPROCFORPREPの値がSSPROPVAL_USEPROCFORPREPONの場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. その接続がデータ ソースの初期化時に作成された既定の接続の場合は、データ ソースの初期化が解除されたときのみ、一時ストアド プロシージャが削除されます。  
  
 SSPROP_INIT_USEPROCFORPREP の値が SSPROPVAL_USEPROCFORPREP_ON_DROP の場合は、OLE DB Driver for SQL Server の一時ストアド プロシージャは、次のいずれかが発生したときに削除されます。  
  
-   コンシューマーは**icommandtext::setcommandtext**を新しいコマンドを示します。  
  
-   コンシューマーは**ICommandPrepare::Unprepare**コマンド テキストを必要がなくなったことを示すためにします。  
  
-   コンシューマーが一時ストアド プロシージャを使用して、コマンド オブジェクトへのすべての参照を解放したとき。  
  
 コマンド オブジェクト最大で 1 つ一時ストアド プロシージャは、 **tempdb**です。 既存の一時ストアド プロシージャは、特定のコマンド オブジェクトに関する現在のコマンド テキストを表します。  
  
## <a name="see-also"></a>参照  
 [[コマンド]](../../oledb/ole-db-commands/commands.md)  
  
  
