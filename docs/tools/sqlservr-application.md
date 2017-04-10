---
title: "sqlservr アプリケーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "コマンド プロンプト ユーティリティ [SQL Server], sqlservr"
  - "コマンド プロンプト [SQL Server], SQL Server インスタンスの一時停止/再開"
  - "SQL Server インスタンスの開始"
  - "コマンド プロンプト [SQL Server], SQL Server インスタンスの続行"
  - "sqlservr ユーティリティ"
  - "SQL Server インスタンスの一時停止"
  - "SQL Server インスタンスの停止"
  - "SQL Server の再開"
  - "コマンド プロンプト [SQL Server], SQL Server インスタンスの停止"
  - "コマンド プロンプト [SQL Server], SQL Server インスタンスの開始"
  - "SQL Server インスタンスの続行"
ms.assetid: 60e8ef0a-0851-41cf-a6d8-cca1e04cbcdb
caps.latest.revision: 39
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 39
---
# sqlservr アプリケーション
  コマンド プロンプトから **sqlservr** アプリケーションを使用して、 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを起動、停止、一時停止、または続行します。  
  
## 構文  
  
```  
  
sqlservr [-sinstance_name] [-c] [-dmaster_path] [-f]   
     [-eerror_log_path] [-lmaster_log_path] [-m]  
     [-n] [-Ttrace#] [-v] [-x] [-gnumber]  
```  
  
## 引数  
 **-s** *instance_name*  
 接続先となる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを指定します。 名前付きインスタンスを指定しない場合、 **sqlservr** は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の既定のインスタンスを起動します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンスを起動する場合、そのインスタンス用の適切なディレクトリで **sqlservr** アプリケーションを使用する必要があります。 既定のインスタンスの場合は、\MSSQL\Binn ディレクトリで **sqlservr** を実行します。 名前付きインスタンスの場合は、\MSSQL$*instance_name*\Binn ディレクトリで **sqlservr** を実行します。  
  
 **-c**  
 Windows サービス コントロール マネージャーに依存せずに、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを起動します。 このオプションは、コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を起動して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の起動に要する時間を短縮する場合に使用します。  
  
> [!NOTE]  
>  ただし、このオプションを使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サービス マネージャーまたは **net stop** コマンドを使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を停止することはできません。また、コンピューターからログオフすると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] は停止します。  
  
 **-d** *master_path*  
 **master** データベース ファイルの完全修飾パスを指定します。 **-d** と *master_path* の間には空白を入れません。 このオプションを省略すると、レジストリ内にあるパラメーターが使用されます。  
  
 **-f**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを最小構成で起動します。 設定値によりサーバーが起動できないとき (たとえば使用できるメモリが不足している場合) などに便利です。  
  
 **-e** *error_log_path*  
 エラー ログ ファイルのフル パスを指定します。 指定しない場合、既定のインスタンスの既定の場所は *\<Drive>*:\Program Files\Microsoft SQL Server\MSSQL\Log\Errorlog で、名前付きインスタンスの既定の場所は *\<Drive>*:\Program Files\Microsoft SQL Server\MSSQL$*instance_name*\Log\Errorlog となります。 **-e** と *error_log_path* の間には空白を入れません。  
  
 **-l** *master_log_path*  
 **master** データベース トランザクション ログ ファイルの完全修飾パスを指定します。 **-l** と *master_log_path* の間には空白を入れません。  
  
 **-m**  
 シングル ユーザー モードで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを起動します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をシングル ユーザー モードで起動した場合、1 人のユーザーのみ接続できます。 CHECKPOINT メカニズムは起動しません。CHECKPOINT メカニズムとは、完了したトランザクションをディスク キャッシュからデータベース デバイスに正しく書き込むことを保証する機能です。 一般的に、システム データベースを修復する必要がある問題が発生したときに、このオプションを使用します。このオプションによって **sp_configure allow updates** オプションが有効になります。 既定の設定では、 **allow updates** は無効になります。  
  
 **-n**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の名前付きインスタンスの起動を可能にします。 **-s** パラメーターを設定しない場合、既定のインスタンスが起動します。 **sqlservr.exe**を開始する前に、コマンド プロンプトで、インスタンスの適切な BINN ディレクトリに移動する必要があります。 たとえば、Instance1 がバイナリ用に \mssql$Instance1 を使用する場合、ユーザーは \mssql$Instance1\binn ディレクトリで **sqlservr.exe -s instance1** を起動する必要があります。 **-n** オプションで [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを起動する場合は、**-e** オプションも使用してください。このオプションを指定しないと、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のイベントは記録されません。  
  
 **-T** *trace#*  
 指定された、有効なトレース フラグ (*trace#*) を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスを起動します。 トレース フラグを使用してサーバーが起動すると、標準的な動作とは異なります。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../Topic/Trace%20Flags%20\(Transact-SQL\).md)」を参照してください。  
  
> [!IMPORTANT]  
>  トレース フラグを指定するときは、 **-T** を使用してトレース フラグ番号を渡してください。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では小文字の t (**-t**) も入力できますが、**-t** では、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のサポート エンジニアが必要とする他の内部トレース フラグが設定されます。  
  
 **-v**  
 サーバーのバージョン番号を表示します。  
  
 **-x**  
 CPU 時間とキャッシュ ヒット率統計の管理を禁止します。 パフォーマンスは最大になります。  
  
 **-g** *memory_to_reserve*  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] メモリ プール外にある [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロセス内に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がメモリ割り当て用の領域として残すメモリの容量を、整数で指定します (メガバイト単位)。 メモリ プール外のメモリは、拡張プロシージャ `.dll` ファイル、分散クエリによって参照される OLE DB プロバイダー、および [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ステートメントで参照されるオートメーション オブジェクトなどのアイテムを読み込むために、[!INCLUDE[tsql](../includes/tsql-md.md)] によって使用される領域です。 既定値は 256 MB です。  
  
 このオプションの使用はメモリの割り当ての調整に役立ちますが、オペレーティング システムによって構成されたアプリケーション用の仮想メモリの制限設定よりも、物理メモリの容量が大きい場合にのみ使用してください。 このオプションは、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] で必要とされるメモリ使用量が通常より多い大容量メモリ構成で、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] プロセスの仮想アドレス領域の全体が使用される場合に効果があります。 このオプションを誤って使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が起動しないことや、実行時エラーが発生することがあります。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エラー ログに次の警告が記録されない限り、**-g** パラメーターの既定値を使用してください。  
  
-   "Failed Virtual Allocate Bytes: FAIL_VIRTUAL_RESERVE \<size>"  
  
-   "Failed Virtual Allocate Bytes: FAIL_VIRTUAL_COMMIT \<size>"  
  
 これらのメッセージは、拡張ストアド プロシージャ .dll ファイルやオートメション オブジェクトなどのアイテムの格納領域を確保するために [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] が [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] メモリ プールの一部を解放しようとしていることを示している場合があります。 その場合は、**-g** スイッチによって確保するメモリ量を増やすことを検討してください。  
  
 既定値より小さい値を使用すると、バッファー プールおよびスレッド スタックが利用できる容量が増えます。その結果、拡張ストアド プロシージャ、分散クエリまたはオートメーション オブジェクトを多用しないシステムの、メモリ負荷の高い作業のパフォーマンスが向上することがあります。  
  
## 解説  
 ほとんどの場合、sqlserver.exe プログラムはトラブルシューティングや主なメンテナンスのみに使用されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] がコマンド プロンプトから sqlservr.exe で起動された場合、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] はサービスとしては起動しないため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] net **コマンドを使用して** を停止することはできません。 ユーザーは [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に接続することができますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ツールによってサービスのステータスが表示されるため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーはサービスが停止されたことを適切に示すことができます。 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] もサーバーに接続することができますが、同じようにサービスが停止されたことを示すことができます。  
  
## 互換性サポート  
 **-h** パラメーターは、[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ではサポートされていません。 このパラメーターは、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 32 ビットのインスタンスで AWE が有効になっている場合に、ホット アド メモリ メタデータ用の仮想メモリ アドレス空間を確保するために使用されていました。 詳細については、[SQL Server 2016 で提供が中止された機能](../Topic/Discontinued%20SQL%20Server%20Features%20in%20SQL%20Server%202016.md)に関するページを参照してください。  
  
## 参照  
 [データベース エンジン サービスのスタートアップ オプション](../database-engine/configure-windows/database-engine-service-startup-options.md)  
  
  