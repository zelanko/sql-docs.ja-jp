---
title: "ドライバー マネージャーの接続がプール |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connection pooling [ODBC]
- pooled connections [ODBC]
- connecting to driver [ODBC], connection pooling
- connecting to data source [ODBC], connection pooling
ms.assetid: ee95ffdb-5aa1-49a3-beb2-7695b27c3df9
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d2883c374768723eeff4100113873130eeea6da7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="driver-manager-connection-pooling"></a>ドライバー マネージャーの接続プール
接続プールを使用するたびに再確立する必要がない接続プールからの接続を使用するアプリケーションを有効にします。 接続が作成され、プールに格納されて、アプリケーションは、完全な接続プロセスを実行しないで、その接続を再利用できます。  
  
 プールされた接続を使用すると、アプリケーションが接続を行うには、オーバーヘッドを保存するために大幅なパフォーマンス向上が発生することができます。 これは、ネットワーク経由で接続する中間層アプリケーションのまたは接続し、切断しても、インターネット アプリケーションなどを繰り返し行うアプリケーションに対して特に重要なことができます。  
  
 パフォーマンスの向上だけでなく、接続プールのアーキテクチャにより、環境とその関連付けられている接続を 1 つのプロセスで複数のコンポーネントで使用します。 これは、互いを認識せず、同じプロセス内のスタンドアロンのコンポーネントが相互にやり取りできることを意味します。 接続プール内の接続は、複数のコンポーネントで繰り返し使用できます。  
  
> [!NOTE]  
>  接続プールは、ODBC 2 が発生している ODBC アプリケーションによって使用できます。*x*動作、アプリケーションが呼び出すことができますとならない限り*SQLSetEnvAttr*です。 アプリケーションがデータベースまたは変更するなどのデータベースのコンテキストを変更する SQL ステートメントを実行する必要がありますされません接続プールを使用する場合、 \<*データベース**名前*>、データ ソースによって使用されるカタログを変更します。  
  
 ODBC ドライバー完全にスレッド セーフでは、接続が接続プールをサポートするスレッドの関係にはできません。 つまり、ドライバーはいつでも任意のスレッドで呼び出しを処理できるとは別のスレッドでの接続を使用して、3 番目のスレッドで切断する 1 つのスレッドで接続できます。  
  
 接続プールには、ドライバー マネージャーでは維持されます。 アプリケーションを呼び出すとき、接続はプールから取り出さ**SQLConnect**または**SQLDriverConnect**アプリケーションを呼び出すときに、プールに返される**SQLDisconnect**. プールのサイズは、要求されたリソースの割り当て状況に基づいて動的に大きくなります。 非アクティブ タイムアウトに基づいてサイズが小さく: 一定の時間 (が使用されていない接続で) の接続がアクティブでない場合は、プールから削除します。 プールのサイズは、メモリの制約と、サーバー上の制限によってのみ制限されます。  
  
 ドライバー マネージャーで渡される引数に基づいて、プール内の特定の接続を使用するかどうかを判断**SQLConnect**または**SQLDriverConnect**と、接続属性に従って接続が割り当てられた後に設定します。  
  
 ドライバー マネージャーは、接続をプールは、ときにかどうか、接続が機能する接続を渡す前に決定できるでなければなりません。 それ以外の場合、ドライバー マネージャーが保持でを配布アプリケーションへの接続を停止している一時的なネットワーク エラーが発生するたびにします。 ODBC 3 で新しい接続属性を定義した*.x*: SQL_ATTR_CONNECTION_DEAD です。 これは読み取り専用接続属性を SQL_CD_TRUE または SQL_CD_FALSE を返します。 SQL_CD_TRUE 値は、接続が失われたこと、SQL_CD_FALSE 値により、接続がアクティブであること、一方を意味します。 (ODBC の以前のバージョンに準拠したドライバーは、この属性をサポートできますも)。  
  
 ドライバーでは、このオプションを効率的に実装する必要があります。 または接続プールのパフォーマンスを品質が低下します。 具体的には、この接続属性を取得する呼び出しでは、サーバーへのラウンド トリップが発生しません必要があります。 代わりに、ドライバーは、接続の最後の既知の状態を返すだけ必要があります。 サーバーへの最後のトリップが失敗した場合は停止していると、最後のトリップが成功した場合にいない配信不能の接続です。  
  
## <a name="remarks"></a>解説  
 接続が失われている場合 (SQL_ATTR_CONNECTION_DEAD 経由で報告されます)、ODBC ドライバー マネージャーは、ドライバーで SQLDisconnect を呼び出すことによってその接続を破棄します。 新しい接続要求がプールで使用可能な接続が見つかりません。 最終的に、ドライバー マネージャーが新しい接続を作成、プールが空であると仮定します。  
  
 接続プールを使用するのには、アプリケーションは、次の手順を実行します。  
  
1.  呼び出しで接続プール機能を有効に**SQLSetEnvAttr** SQL_CP_ONE_PER_DRIVER または SQL_CP_ONE_PER_HENV SQL_ATTR_CONNECTION_POOLING 環境属性を設定します。 アプリケーションがどの接続のプールを有効にするのには、共有環境を割り当てる前に、この呼び出しを実行する必要があります。 呼び出しで、環境ハンドル**SQLSetEnvAttr** SQL_ATTR_CONNECTION_POOLING プロセス レベルの属性は、null に設定する必要があります。 属性が SQL_CP_ONE_PER_DRIVER に設定されている場合は、各ドライバーの 1 つの接続プールがサポートされています。 アプリケーションは、ドライバーの多くといくつかの環境で動作する場合がありますより効率的な数の比較が必要な可能性があります。 SQL_CP_ONE_PER_HENV、単一の接続プールに設定が各環境をサポート場合します。 アプリケーションは、多くの環境およびいくつかのドライバーで動作する場合がありますより効率的な少ない比較が必要な可能性があります。 SQL_CP_OFF SQL_ATTR_CONNECTION_POOLING に設定して、接続プールを無効になっています。  
  
2.  呼び出すことによって環境を割り当てます**SQLAllocHandle**で、 *HandleType*引数 SQL_HANDLE_ENV に設定します。 この呼び出しによって割り当てられている環境には接続プールを有効になっているために、暗黙的な共有環境になります。 使用する環境は決まっていませんただし、まで**SQLAllocHandle**で、 *HandleType* sql_handle_dbc としてのこのような環境で呼び出されます。  
  
3.  呼び出して接続を割り当てます**SQLAllocHandle**で*InputHandle* sql_handle_dbc としてに設定され、 *InputHandle*に割り当てられている環境ハンドルに設定プールに接続します。 ドライバー マネージャーは、アプリケーションによって設定される環境属性に一致する既存の環境を検索しようとします。 このような環境が存在しない場合、いずれかが作成され、1 の参照カウント (ドライバー マネージャーによって維持されます)。 一致する共有環境が見つかった場合、環境は、アプリケーションに返され、参照カウントがインクリメントされます。 (使用する実際の接続がまでドライバー マネージャーによって決定されない**SQLConnect**または**SQLDriverConnect**と呼びます)。  
  
4.  呼び出し**SQLConnect**または**SQLDriverConnect**接続を確立します。 ドライバー マネージャーへの呼び出しで、接続オプションを使用して**SQLConnect** (またはへの呼び出しで接続キーワード**SQLDriverConnect**)、接続属性を設定する接続の割り当て後に、プール内のどの接続を使用する必要がありますを決定します。  
  
    > [!NOTE]  
    >  要求された接続が照合されているプールされた接続する方法については、SQL_ATTR_CP_MATCH 環境属性によって決まります。 詳細については、次を参照してください。 [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)です。  
  
     接続プールを使用する ODBC アプリケーションで呼び出す必要があります[CoInitializeEx](http://go.microsoft.com/fwlink/?LinkID=116307)アプリケーション初期化中に、 [CoUninitialize](http://go.microsoft.com/fwlink/?LinkId=116310)アプリケーションを閉じたときです。  
  
5.  呼び出し**SQLDisconnect**接続で実行時にします。 接続は、接続プールに返され、再利用できるようになります。  
  
 詳細については、次を参照してください。 [Microsoft Data Access Components のプール](http://go.microsoft.com/fwlink/?LinkId=120776)です。  
  
## <a name="connection-pooling-considerations"></a>接続プールの考慮事項  
 SQL コマンドを使用して次の操作の (ではなく、ODBC API を使用) のいずれかを実行、接続の状態に影響し、接続プールがアクティブなときに予期しない問題が発生することができます。  
  
-   接続を開き、既定のデータベースを変更します。  
  
-   構成可能なオプション (SET ROWCOUNT、ANSI_、IMPLICIT_TRANSACTIONS、実行プラン、統計、TEXTSIZE、および DATEFORMAT を含む) を変更するのにには、SET ステートメントを使用します。  
  
-   一時テーブルとストアド プロシージャを作成しています。  
  
 ODBC API の外部でこれらのアクションのいずれかが実行される場合、接続を使用する次のユーザーは以前の設定、テーブル、またはプロシージャを自動的に継承します。  
  
> [!NOTE]  
>  接続の状態に存在する特定の設定を期待できません。 常に、アプリケーションで接続状態を設定し、アプリケーションがすべて使用されていない接続プールの設定を削除することを確認する必要があります。  
  
## <a name="driver-aware-connection-pooling"></a>ドライバー対応接続プール  
 Windows 8 以降では、ODBC ドライバーことができます接続プールでより効率的に使用します。 詳細については、次を参照してください。[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。  
  
## <a name="see-also"></a>参照  
 [データに接続するソースまたはドライバー](../../../odbc/reference/develop-app/connecting-to-a-data-source-or-driver.md)   
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [Microsoft Data Access Components のプール](http://go.microsoft.com/fwlink/?LinkId=120776)
