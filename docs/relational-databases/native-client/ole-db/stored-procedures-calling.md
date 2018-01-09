---
title: "ストアド プロシージャ (OLE DB) を呼び出す |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [SQL Server Native Client], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: 8e5738e5-4bbe-4f34-bd69-0c0633290bdd
caps.latest.revision: "39"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: caf634af86e7338d25ae18a2101cffabb9f5f762
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="stored-procedures---calling"></a>ストアド プロシージャの呼び出し
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ストアド プロシージャは、0 個以上のパラメーターを受け取ることができます。 また、値を返すこともできます。 使用する場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、ストアド プロシージャのパラメーターは、渡すことができます。  
  
-   データ値をハードコーディングする。  
  
-   パラメーター マーカー (?) を使用してパラメーターを指定し、プログラム変数をパラメーター マーカーにバインドしてから、データ値をプログラム変数に格納する。  
  
> [!NOTE]  
>  OLE DB で名前付きパラメーターを使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ストアド プロシージャを呼び出す場合は、パラメーター名の先頭に '@' 文字を付ける必要があります。 これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の制限です。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、この制限を MDAC よりも厳密に適用します。  
  
 パラメーターをサポートする、 **ICommandWithParameters**コマンド オブジェクトでインターフェイスを公開します。 パラメーターを使用するコンシューマー最初パラメーターについて説明します、プロバイダーを呼び出すことによって、 **icommandwithparameters::setparameterinfo**メソッド (または必要に応じて呼び出す呼び出し元のステートメントを準備、 **GetParameterInfo**メソッド)。 次に、バッファーの構造を指定するアクセサーを作成し、このバッファーにパラメーター値を格納します。 最後にバッファーにアクセサーと、ポインターのハンドルを渡す**Execute**です。 以降の呼び出しの**Execute**、コンシューマーでは、新しいパラメーターの値を格納バッファーとの呼び出しで**Execute**アクセサー ハンドルとバッファー ポインターを使用します。  
  
 パラメーターを使用して、一時ストアド プロシージャを呼び出すコマンドを呼び出す必要がありますまず**icommandwithparameters::setparameterinfo**コマンドを正常に準備する前に、パラメーター情報を定義します。 これは、一時ストアド プロシージャの内部名がクライアントで使用される外部名とは異なるので、SQLOLEDB がシステム テーブルをクエリして、一時ストアド プロシージャのパラメーター情報を判断できないためです。  
  
 次に、パラメーターのバインド プロセスの手順を示します。  
  
1.  DBPARAMBINDINFO 構造体の配列にパラメーター情報を格納します。パラメーター情報には、パラメーター名、パラメーターのデータ型を表すプロバイダー固有の名前、標準のデータ型名などが含まれます。 配列内の構造体 1 つが、1 つのパラメーターを表します。 この配列に渡され、 **SetParameterInfo**メソッドです。  
  
2.  呼び出す、 **icommandwithparameters::setparameterinfo**パラメーターをプロバイダーを記述するメソッド。 **SetParameterInfo**各パラメーターのネイティブ データ型を指定します。 **SetParameterInfo**引数は。  
  
    -   型情報を設定するパラメーターの数  
  
    -   型情報を設定するパラメーターの序数の配列  
  
    -   DBPARAMBINDINFO 構造体の配列  
  
3.  使用してパラメーター アクセサーを作成、 **iaccessor::createaccessor**コマンド。 このアクセサーにより、バッファーの構造を指定し、パラメーター値をバッファーに格納します。 **CreateAccessor**コマンドでは、バインドのセットからアクセサーを作成します。 このバインドは、コンシューマーが DBBINDING 構造体の配列を使用して記述します。 各バインドでは、1 つのパラメーターをコンシューマーのバッファーに関連付けます。バインドには、次のような情報が含まれます。  
  
    -   バインドが適用されるパラメーターの序数  
  
    -   バインドの対象 (データ値、データ値の長さと状態)  
  
    -   これらの各情報に関するバッファー内のオフセット  
  
    -   コンシューマーのバッファー内にあるデータ値の長さと型  
  
     アクセサーは、アクセサーのハンドルにより識別されます。このハンドルは HACCESSOR 型です。 このハンドルは、によって返される、 **CreateAccessor**メソッドです。 コンシューマーが、コンシューマーはアクセサーを使用して完了するとときに、呼び出す必要があります、 **ReleaseAccessor**を保持しているメモリを解放するメソッド。  
  
     ときに、メソッドの呼び出し、コンシューマーなど**icommand::execute**ハンドル、アクセサーとバッファー自体へのポインターを渡します。 プロバイダーはこのアクセサーを使用して、バッファー内にあるデータを送信する方法を決定します。  
  
4.  DBPARAMS 構造体にデータを格納します。 コンシューマーの変数の値の取得元とする入力パラメーターと出力パラメーターの値が書き込まれますが、実行時に渡される**icommand::execute** DBPARAMS 構造体にします。 DBPARAMS 構造体には、次の 3 つの要素が含まれます。  
  
    -   アクセサー ハンドルで指定されているバインドに従ってプロバイダーが入力パラメーター データを取得し、出力パラメーター データを返すための、バッファーへのポインター  
  
    -   バッファー内のパラメーター セットの数  
  
    -   手順 3. で作成したアクセサー ハンドル  
  
5.  使用して、コマンドを実行**icommand::execute**です。  
  
## <a name="methods-of-calling-a-stored-procedure"></a>ストアド プロシージャを呼び出す方法  
 内のストアド プロシージャを実行するときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーをサポートします。  
  
-   ODBC CALL エスケープ シーケンスです。  
  
-   リモート プロシージャ コール (RPC) エスケープ シーケンス  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE ステートメント  
  
### <a name="odbc-call-escape-sequence"></a>ODBC 呼び出しエスケープ シーケンス  
 パラメーター情報がわかっている場合は、呼び出す**icommandwithparameters::setparameterinfo**パラメーターをプロバイダーを記述するメソッド。 それ以外の場合は、ストアド プロシージャの呼び出しに ODBC CALL 構文を使用すると、プロバイダーはヘルパー関数を呼び出してストアド プロシージャのパラメーター情報を取得します。  
  
 パラメーター情報 (パラメーターのメタデータ) を把握していない場合は、ODBC CALL 構文の使用をお勧めします。  
  
 ODBC CALL エスケープ シーケンスを使用してプロシージャを呼び出す場合の一般的な構文は、次のとおりです。  
  
 {**[? =]****呼び出す***procedure_name*[**(**[*パラメーター*] [**、**[*パラメーター*].**)**]}  
  
 例 :  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a>RPC エスケープ シーケンス  
 RPC エスケープ シーケンスは、ストアド プロシージャを呼び出す ODBC CALL 構文と似ています。 プロシージャを複数回呼び出す場合は、ストアド プロシージャを呼び出す 3 つの方法のうち、RPC エスケープ シーケンスのパフォーマンスが最も優れています。  
  
 RPC エスケープ シーケンスを使用してストアド プロシージャを実行する場合、プロバイダーはパラメーター情報の決定にヘルパー関数を呼び出しません (ODBC CALL 構文では、ヘルパー関数が呼び出されます)。 RPC 構文は ODBC CALL 構文よりも簡単です。そのためコマンドが高速に解析され、パフォーマンスが向上します。 この場合、実行することによって、パラメーター情報を指定する必要があります**icommandwithparameters::setparameterinfo**です。  
  
 RPC エスケープ シーケンスを使用する場合は、戻り値が必要です。 ストアド プロシージャが値を返さない場合、サーバーが既定で 0 を返します。 また、ストアド プロシージャ上で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソルを開くことはできません。 ストアド プロシージャは暗黙的に準備をする呼び出しと**icommandprepare::prepare**は失敗します。 できないのため、RPC 呼び出しを準備する、できますクエリを実行しない列のメタデータです。Icolumnsinfo::getcolumninfo と icolumnsrowset::getcolumnsrowset は db_e_notprepared します。  
  
 パラメーターのメタデータを把握できている場合は、ストアド プロシージャの実行方法として RPC エスケープ シーケンスの使用をお勧めします。  
  
 次に、ストアド プロシージャを呼び出す RPC エスケープ シーケンスの例を示します。  
  
```  
{rpc SalesByCategory}  
```  
  
 RPC エスケープ シーケンスを示すサンプル アプリケーションを参照してください[ストアド プロシージャ &#40; を実行。RPC 構文 &#41; を使用します。リターン コードと出力パラメーター &#40; OLE DB &#41; の処理](../../../relational-databases/native-client-ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md).  
  
### <a name="transact-sql-execute-statement"></a>Transact-SQL EXECUTE ステートメント  
 ODBC CALL エスケープ シーケンスおよび RPC エスケープ シーケンスは、ストアド プロシージャの呼び出しに推奨される方法ではなく、 [EXECUTE](../../../t-sql/language-elements/execute-transact-sql.md)ステートメントです。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、の RPC 機構[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]コマンドの処理を最適化します。 この RPC プロトコルでは、サーバー側で実行されるパラメーター処理やステートメントの解析作業の多くを排除することで、パフォーマンスを向上しています。  
  
 これは、例、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE**ステートメント。  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
