---
title: ODBC ドライバー対応接続プールの開発 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 795fa0d91e706b2c78bd12f492413ca10a04d35b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>ODBC ドライバー対応接続プールの開発
このトピックでは、ドライバーが接続プールのサービスを提供する方法に関する情報を含む ODBC ドライバーの開発の詳細について説明します。  
  
## <a name="enabling-driver-aware-connection-pooling"></a>ドライバー対応接続プールを有効にします。  
 ドライバーは、次の ODBC サービス プロバイダー インターフェイス (SPI) 関数を実装する必要があります。  
  
-   SQLSetConnectAttrForDbcInfo  
  
-   SQLSetConnectInfo  
  
-   SQLSetDriverConnectInfo  
  
-   SQLGetPoolID  
  
-   SQLRateConnection  
  
-   SQLPoolConnect  
  
-   SQLCleanupConnectionPoolID  
  
 参照してください[ODBC サービス プロバイダー インターフェイス (SPI) 参照](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)詳細についてはします。  
  
 ドライバー対応のプールを有効にすることができるようにドライバーも次の既存の関数を実装する必要があります。  
  
|関数|追加された機能|  
|--------------|-------------------------|  
|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|新しいハンドル型のサポート: SQL_HANDLE_DBC_INFO_TOKEN (以下の説明を参照してください)。|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|新しい設定専用の接続属性をサポート: 接続をリセットするための SQL_ATTR_DBC_INFO_TOKEN (以下の説明を参照してください)。|  
  
> [!NOTE]  
>  使用されなくなった関数をなど**SQLError**と**SQLSetConnectOption**ドライバー対応接続プールはサポートされていません。  
  
## <a name="the-pool-id"></a>プール ID  
 プール ID は、同じ意味で使用できる接続の特定のグループを表すポインター長さドライバー固有 ID です。 接続情報を指定するドライバーがありますを迅速に対応するプールの ID を推測するには  
  
 たとえば、プールの ID は、サーバー名と資格情報をエンコードする必要があります。 ただし、ドライバーは接続を再利用し、新しい接続を確立するよりも短時間で、データベースを変更できる場合がありますので、データベース名は必要ありません。  
  
 ドライバーはプール ID を構成するキーの属性のセットを定義する必要があります。 これらのキー属性の値は、接続属性、接続文字列、および DSN から取得できます。 これらのソースでの競合があるような場合は、旧バージョンとの互換性のため、ドライバー固有の既存の解決方法を使用してください。  
  
 ドライバー マネージャーでは、別のプールを別のプールの Id を使用します。 同じプール内のすべての接続は、再利用します。 ドライバー マネージャーが別のプールの ID を持つ接続を再利用しません。  
  
 したがってドライバーは、定義済みのキー属性に同じ値を持つ接続のすべてのグループの一意のプールの ID を割り当てる必要があります。 ドライバーは、そのキー属性の値が異なる 2 つの接続のプールと同じ ID を使用している場合、ドライバー マネージャーは配置に (ドライバー マネージャーを使うと、ドライバー固有のキー属性について何も知っている)、同じプールにです。 これは、ドライバーは、ドライバー マネージャーに異なる一連のキー属性との接続は内部再利用可能ではないを報告する必要があることを意味[SQLRateConnection 関数](../../../odbc/reference/syntax/sqlrateconnection-function.md)です。 パフォーマンスが低下することができ、これは推奨されません。  
  
 ドライバー マネージャーには、すべての接続情報と一致する場合でも、別のドライバー環境から割り当てられた接続が再利用されます。 ドライバー マネージャーが使用して別のプールの別の環境の接続があるプール ID が同じ場合でも したがって、プール ID は、そのドライバー環境に対してローカルです。  
  
 ドライバーからプール ID を取得するため、関数は[SQLGetPoolID 関数](../../../odbc/reference/syntax/sqlgetpoolid-function.md)です。  
  
## <a name="the-connection-rating"></a>接続の評価  
 比較して、新しい接続を確立、プールされた接続の一部の接続情報 (データベースなど) をリセットすることによってパフォーマンスが向上を取得できます。 そのため、データベース名、キー属性のセット内にあるしない可能性があります。 それ以外の場合、顧客がさまざまな異なる接続文字列を使用してデータベースごとに、中間層アプリケーションで適切なできない可能性があります、独立したプールすることができます。  
  
 返される接続がこのアプリケーションの要求と同じになるよう、新しいアプリケーションの要求に基づいてが一致しない属性をリセットする必要がありますをいくつかの属性の不一致を持つ接続を再利用するたびに (SQL_ATTR 属性の説明を参照してください。_DBC_INFO_TOKEN [SQLSetConnectAttr 関数](http://go.microsoft.com/fwlink/?LinkId=59368))。 ただし、これらの属性をリセットするとパフォーマンスが低下する可能性があります。 たとえば、データベースをリセットするには、サーバーへのネットワーク呼び出しが必要です。 そのため、1 つが利用可能な場合が完全に一致する接続を再利用します。  
  
 ドライバーで評価関数は、新しい接続要求に既存の接続を評価できます。 たとえば、ドライバーの評価の関数を特定します。  
  
-   場合は、既存の接続には、要求は完全に照合されます。  
  
-   のみいくつか意味のない不一致、接続タイムアウトなどをリセットするサーバーとの通信を必要としない場合。  
  
-   リセットするには、サーバーとの通信を必要とするが、新しい接続を確立するよりも優れたパフォーマンスにもなるいくつかの一致しない属性がある場合。  
  
-   不一致が発生したかどうかにリセットする非常に時間がかかる場合は、属性の (ドライバーの開発者が考えにプール ID の生成に使用される一連のキー属性は、この属性を追加する)。  
  
 0 ~ 100 の間のスコアは、可能な限り、0 の場合は再利用しない、100、つまりと完全に一致します。 [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)接続を評価する関数です。  
  
## <a name="new-odbc-handle---sqlhandledbcinfotoken"></a>新しい ODBC ハンドル - SQL_HANDLE_DBC_INFO_TOKEN  
 ドライバーをドライバー対応接続プールをサポートするには、コンピューティング、プールの ID への接続情報が必要 ドライバーでは、接続情報、プール内の接続で新しい接続要求を比較する必要もあります。  プール内の接続を再利用できるいない、ときに、ドライバーは接続情報を必要とするため、新しい接続を確立するためには。  
  
 接続情報は、複数のソース (接続文字列、接続属性、および DSN) から取得できます、ためドライバーが接続文字列を解析し、これらの上の関数呼び出しの各ソース間の競合を解決する必要があります。  
  
 したがって、新しい ODBC ハンドルが導入されました。 SQL_HANDLE_DBC_INFO_TOKEN です。 SQL_HANDLE_DBC_INFO_TOKEN で、ドライバーは接続文字列を解析し、接続情報の競合を解決するには、2 回以上は必要ありません。 これは、ドライバー固有のデータ構造であるため、ドライバーは接続情報などのデータを格納またはプールの id。  
  
 このハンドルは、ドライバー マネージャーとドライバーの間のインターフェイスとしてのみ使用します。 アプリケーションは、このハンドルを直接割り当てることはできません。  
  
 このハンドルの親ハンドルは型 SQL_HANDLE_ENV、つまり、ドライバーが接続情報の解決時に、HENV ハンドルから環境情報を取得できるようにします。  
  
 新しい接続要求を受信したときに、ドライバー マネージャーは、接続情報を格納すると、ドライバーが接続プールの認識をサポートしていることを確認した後の型 SQL_HANDLE_DBC_INFO_TOKEN のハンドルを割り当てられます。 ハンドルを使用して完了したら (を返す前に、いくつかのリターン コードを SQL_STILL_EXECUTING 以外が[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)または[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md))、ドライバー マネージャーは、ハンドルを解放します。 そのため、ハンドルでは、SQLAllocHandle 呼び出しの後に作成され、SQLFreeHandle 呼び出しの後に破棄されます。 ドライバー マネージャーにより、関連付けられている HENV を解放する前に、ハンドルが解放されます (ときに[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)または[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)エラーが返されます)。  
  
 ドライバーは、新しいハンドル型 SQL_HANDLE_DBC_INFO_TOKEN を受け入れるように、次の関数を変更する必要があります。  
  
1.  [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 ドライバー マネージャーは、複数のスレッドが同じ SQL_HANDLE_DBC_INFO_TOKEN ハンドルを同時に使用していないことを保証します。 そのため、このハンドルの同期化モデルはドライバー内部の非常に簡単にできます。 ドライバー マネージャーの割り当てと SQL_HANDLE_DBC_INFO_TOKEN を解放する前に、環境のロックになりません。  
  
 ドライバー マネージャーの**SQLAllocHandle**と**SQLFreeHandle**この新しい種類のハンドルを受け入れません。  
  
 SQL_HANDLE_DBC_INFO_TOKEN には、資格情報などの機密情報を含めることがあります。 そのため、ドライバーは安全にバッファーをクリアしますメモリ (を使用して[SecureZeroMemory](http://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)) を使用してこのハンドルを解放する前に機密性の高い情報を含む**SQLFreeHandle**です。 アプリケーションの環境ハンドルが閉じているときにすべての関連付けられている接続プールは閉じられます。  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>ドライバー マネージャーの接続プールがアルゴリズムの評価  
 このセクションでは、ドライバー マネージャーの接続プールの評価のアルゴリズムについて説明します。 ドライバーの開発者は、旧バージョンとの互換性のため、同じアルゴリズムを実装できます。 このアルゴリズムは、最適なものをできない可能性があります。 これを調整する必要があります、実装に基づくアルゴリズム (それ以外の場合はこの機能を実装する理由)。  
  
 ドライバー マネージャーはプールから接続ごとに 100、0 から整数の評価を返します。 0 は、接続が再利用できない場合を示し、100、完全一致を表します。 接続要求が hRequest をという名前でプールから既存の接続の hCandidate として名前があるとします。 次の条件のいずれかが false の場合、プールされた接続 hCandidate が hRequest (ドライバー マネージャーは、レベル 0 を割り当てられます) の再利用できません。  
  
-   hCandidate と hRequest (SQLDriverConnectW) などの UNICODE API または ANSI API (SQLDriverConnectA) などのいずれかに起因します。 (UNICODE ドライバーには、さまざまな ANSI API および UNICODE API (SQL_ATTR_ANSI_APP 接続属性を参照してください) を指定の動作ことができます)。  
  
-   hCandidate と hRequest が関数によって作成された、同じです。SQLDriverConnect または SQLConnect のいずれか。  
  
-   SQLDriverConnect を使用する場合は、hCandidate を開くために使用する接続文字列は hRequest と同じでなければなりません。  
  
-   サーバー名 (DSN)、ユーザー名と hCandidate を開くために使用するパスワードには、同じ SQLConnect を使用する場合は、hRequest を開くために使用する必要があります。  
  
-   HCandidate を開くために使用する SID とは、現在のスレッドのセキュリティ識別子 (SID) は同じである必要があります。  
  
-   参加および参加解除するにはコストがドライバー (で SQL_DTC_TRANSITION_COST の説明を参照して[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md))、再利用*hRequest*余分な参加または参加解除が必要としない必要があります。  
  
 次の表は、さまざまなシナリオのスコアの割り当てを示します。  
  
|プールされた接続と要求の間の接続属性の比較|なしの参加/参加解除|余分な参加する必要は/参加解除|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|カタログ (SQL_ATTR_CURRENT_CATALOG) が異なる|60|50|  
|いくつかの接続属性異なりますが、カタログは同じ|90|70|  
|完全に一致するすべての接続属性|100|80|  
  
## <a name="sequence-diagram"></a>シーケンス図  
 このシーケンス図は、このトピックで説明されているプールの基本的なメカニズムを示します。 使用だけが表示[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)ですが、 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)ケースに似ています。  
  
 ![シーケンス ダイアグラム](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>状態ダイアグラム  
 この状態の図は、接続情報のトークン オブジェクト、このトピックで説明を示します。 のみの図に[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)ですが、 [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)ケースに似ています。 ドライバー マネージャーを呼び出すことができます、ドライバー マネージャーは、いつでもエラーを処理する必要があります、ため[SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)のいずれかの状態。  
  
 ![状態の図](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>参照  
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC サービス プロバイダー インターフェイス (SPI) リファレンス](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
