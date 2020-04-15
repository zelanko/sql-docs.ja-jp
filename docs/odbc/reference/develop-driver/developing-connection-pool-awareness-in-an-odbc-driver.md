---
title: ODBC ドライバでの接続プール認識の開発 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c63d5cae-24fc-4fee-89a9-ad0367cddc3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f77fea1d8439ac9ce7374b7dd47db5665686cfbc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283432"
---
# <a name="developing-connection-pool-awareness-in-an-odbc-driver"></a>ODBC ドライバー対応接続プールの開発
このトピックでは、ドライバーが接続プール サービスを提供する方法に関する情報を含む ODBC ドライバーの開発の詳細について説明します。  
  
## <a name="enabling-driver-aware-connection-pooling"></a>ドライバー対応接続プールの有効化  
 ドライバーは、次の ODBC サービス プロバイダー インターフェイス (SPI) 関数を実装する必要があります。  
  
-   を使用します。  
  
-   接続情報  
  
-   接続情報  
  
-   を使用します。  
  
-   接続  
  
-   コネクト  
  
-   接続プール ID  
  
 詳細については[、ODBC サービス プロバイダー インターフェイス (SPI) リファレンス](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)を参照してください。  
  
 ドライバー対応プーリングを有効にできるように、ドライバーは、次の既存の関数も実装する必要があります。  
  
|機能|機能の追加|  
|--------------|-------------------------|  
|[ハンドル](../../../odbc/reference/syntax/sqlallochandle-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)<br /><br /> [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)<br /><br /> [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|新しいハンドルタイプをサポートします: SQL_HANDLE_DBC_INFO_TOKEN (以下の説明を参照してください)。|  
|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|新しいセット専用接続属性をサポートする:接続をリセットするためのSQL_ATTR_DBC_INFO_TOKEN(以下の説明を参照してください)。|  
  
> [!NOTE]  
>  SQL エラーや**SQLError****SQLSetConnect オプション**などの非推奨の関数は、ドライバー対応接続プールではサポートされていません。  
  
## <a name="the-pool-id"></a>プール ID  
 プール ID は、ポインター長ドライバー固有の ID で、同じ意味で使用できる接続の特定のグループを表します。 接続情報のセットを指定すると、ドライバーは、対応するプール ID をすばやく推測できる必要があります。  
  
 たとえば、プール ID はサーバー名と資格情報をエンコードする必要があります。 ただし、ドライバが接続を再利用し、新しい接続を行うよりも短時間でデータベースを変更できるため、データベース名は必要ありません。  
  
 ドライバーは、プール ID を構成するキー属性のセットを定義する必要があります。 これらのキー属性の値は、接続属性、接続文字列、および DSN から取得できます。 これらのソースに競合がある場合は、下位互換性のために既存のドライバー固有の解決ポリシーを使用する必要があります。  
  
 ドライバー マネージャーは、異なるプールの ID に別のプールを使用します。 同じプール内のすべての接続は再利用可能です。 ドライバー マネージャーは、別のプール ID を持つ接続を再利用することはありません。  
  
 したがって、ドライバーは、定義されたキー属性で同じ値を持つ接続のグループごとに一意のプール ID を割り当てる必要があります。 ドライバーは、キー属性の異なる値を持つ 2 つの接続に同じプール ID を使用する場合、ドライバー マネージャーは、同じプールに配置されます (ドライバー マネージャーは、ドライバー固有のキー属性について何も知りません)。 つまり、ドライバは、異なるキー属性セットを持つ接続が[SQLRateConnection 関数](../../../odbc/reference/syntax/sqlrateconnection-function.md)内で再利用可能ではないことをドライバ マネージャに報告する必要があります。 これによりパフォーマンスが低下する可能性があり、これは推奨されません。  
  
 ドライバー マネージャーは、すべての接続情報が一致する場合でも、別のドライバー環境から割り当てられた接続を再利用しません。 ドライバー マネージャーは、接続が同じプール ID を持つ場合でも、異なる環境に異なるプールを使用します。 したがって、プール ID は、そのドライバー環境にローカルです。  
  
 ドライバーからプール ID を取得するための関数は[、SQLGetPoolID 関数です](../../../odbc/reference/syntax/sqlgetpoolid-function.md)。  
  
## <a name="the-connection-rating"></a>接続の評価  
 新しい接続を確立する場合と比較すると、プールされた接続で一部の接続情報 (DATABASE など) をリセットすることで、パフォーマンスを向上させることができます。 したがって、データベース名をキー属性のセットに含めたくない場合があります。 そうしないと、データベースごとに別々のプールを作成できますが、顧客がさまざまな接続文字列を使用する中間層アプリケーションでは適さない場合があります。  
  
 属性の不一致がある接続を再利用する場合は、新しいアプリケーション要求に基づいて一致しない属性をリセットして、返された接続がアプリケーション要求と同じになるようにする必要があります[(SQLSetConnectAttr 関数](https://go.microsoft.com/fwlink/?LinkId=59368)の属性SQL_ATTR_DBC_INFO_TOKENの説明を参照)。 ただし、これらの属性をリセットすると、パフォーマンスが低下する可能性があります。 たとえば、データベースをリセットするには、サーバーへのネットワーク呼び出しが必要です。 したがって、完全に一致している接続があれば、その接続を再利用してください。  
  
 ドライバーの評価関数は、新しい接続要求を使用して既存の接続を評価できます。 たとえば、ドライバーの評価関数は、次の項目を決定できます。  
  
-   既存の接続が要求と完全に一致している場合。  
  
-   接続タイムアウトなど、リセットするサーバーとの通信を必要としない、一部の不適切な不一致が存在する場合。  
  
-   リセットするためにサーバーとの通信を必要とする属性が一致しない場合でも、新しい接続を確立するよりもパフォーマンスが向上します。  
  
-   リセットに非常に時間がかかる属性に対して不一致が発生した場合 (ドライバーの開発者は、この属性を、プール ID の生成に使用されるキー属性のセットに追加することを検討する場合があります)。  
  
 0 から 100 までのスコアは可能で、0 は再利用しないことを意味し、100 は完全に一致していることを意味します。 [接続を評価](../../../odbc/reference/syntax/sqlrateconnection-function.md)するための関数です。  
  
## <a name="new-odbc-handle---sql_handle_dbc_info_token"></a>新しい ODBC ハンドル - SQL_HANDLE_DBC_INFO_TOKEN  
 ドライバー対応接続プールをサポートするには、ドライバーは、プール ID を計算する接続情報が必要です。 ドライバーは、プール内の接続と新しい接続要求を比較するために接続情報も必要です。  プール内の接続を再利用できない場合は、ドライバーは新しい接続を確立する必要があるため、接続情報が必要になります。  
  
 接続情報は複数のソース (接続文字列、接続属性、および DSN) から取得できるため、ドライバーは接続文字列を解析し、上記の関数呼び出しの各ソース間の競合を解決する必要があります。  
  
 したがって、新しい ODBC ハンドルが導入されました: SQL_HANDLE_DBC_INFO_TOKEN。 SQL_HANDLE_DBC_INFO_TOKENを使用すると、ドライバーは接続文字列を解析し、接続情報の競合を複数回解決する必要はありません。 これはドライバー固有のデータ構造であるため、ドライバーは、接続情報やプール ID などのデータを格納できます。  
  
 このハンドルは、ドライバー マネージャーとドライバーの間のインターフェイスとしてのみ使用されます。 アプリケーションは、このハンドルを直接割り当てることはできません。  
  
 このハンドルの親ハンドルはSQL_HANDLE_ENV型であるため、ドライバーは接続情報の解決時に HENV ハンドルから環境情報を取得できます。  
  
 新しい接続要求を受信するたびに、ドライバー マネージャーは、接続情報を格納するためのSQL_HANDLE_DBC_INFO_TOKEN型のハンドルを割り当てます。ドライバーが接続プールの認識をサポートしていることを確認します。 ハンドルの使用が終了すると (ただし[、SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)または[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)からSQL_STILL_EXECUTING以外のリターン コードを返す前に)、ドライバー マネージャーはハンドルを解放します。 したがって、ハンドルは、呼び出しの後に作成され、SQLFreeHandle 呼び出しの後に破棄されます。 ドライバー マネージャーは、ハンドルが[(SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)または[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)がエラーを返すとき) に関連付けられている HENV を解放する前に解放されることを保証します。  
  
 ドライバーは、新しいハンドルの種類SQL_HANDLE_DBC_INFO_TOKENを受け入れるように、次の関数を変更する必要があります。  
  
1.  [ハンドル](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
2.  [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)  
  
3.  [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
4.  [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
 ドライバー マネージャーは、複数のスレッドが同時に同じSQL_HANDLE_DBC_INFO_TOKENハンドルを使用しないことを保証します。 したがって、このハンドルの同期モデルは、ドライバー内で非常に単純なことができます。 ドライバー マネージャーは、割り当て、SQL_HANDLE_DBC_INFO_TOKENを解放する前に環境ロックを取りません。  
  
 ドライバー マネージャーの**SQLAllocHandle**と**SQLFreeHandle**は、この新しいハンドルの種類を受け入れません。  
  
 SQL_HANDLE_DBC_INFO_TOKENには、資格情報などの機密情報が含まれている場合があります。 したがって、ドライバーは **、SQLFreeHandle**でこのハンドルを解放する前に、機密情報を含むメモリ バッファーを安全にクリアする必要があります ( [SecureZeroMemory](https://msdn.microsoft.com/library/windows/desktop/aa366877\(v=vs.85\).aspx)を使用 ) 。 アプリケーションの環境ハンドルが閉じられると、関連付けられているすべての接続プールが閉じられます。  
  
## <a name="driver-manager-connection-pool-rating-algorithm"></a>ドライバー マネージャー接続プール評価アルゴリズム  
 このセクションでは、ドライバー マネージャー接続プールの評価アルゴリズムについて説明します。 ドライバー開発者は、下位互換性のために同じアルゴリズムを実装できます。 このアルゴリズムは最適ではないかもしれません。 実装に基づいてこのアルゴリズムを調整する必要があります (そうでない場合は、この機能を実装する理由はありません)。  
  
 ドライバー マネージャーは、プールからの接続ごとに 0 から 100 までの整数評価を返します。 0 は接続を再利用できないことを示し、100 は完全一致を示します。 接続要求の名前が hRequest と、プールからの既存の接続の名前が hCandidate とします。 次のいずれかの条件が false の場合、プールされた接続 hCandidate を hRequest に再利用することはできません (ドライバー マネージャーは 0 の評価を割り当てます)。  
  
-   h候補と h要求の両方が、UNICODE API (SQLDriverConnectW など) または ANSI API (SQLDriverConnectA など) のいずれかから取得されます。 (UNICODE ドライバーは、ANSI API と UNICODE API を指定して動作が異なる場合があります (接続属性SQL_ATTR_ANSI_APP参照)。  
  
-   hCandidate と hRequest は同じ関数で作成されます。または接続します。  
  
-   開くために使用される接続文字列は、sqlDriverConnect を使用する場合は、hRequest と同じである必要があります。  
  
-   [候補] を開くために使用するサーバー名 (DSN) 、ユーザー名、およびパスワードは、SQLConnect を使用する場合に hRequest を開くときに使用するパスワードと同じにする必要があります。  
  
-   現在のスレッドのセキュリティ識別子 (SID) は、hCandidate を開くために使用される SID と同じである必要があります。  
  
-   参加と参加解除にコストがかかるドライバ[(SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)のSQL_DTC_TRANSITION_COSTの説明を参照) の場合 *、hRequest*を再利用するには追加の参加または参加解除を必要としません。  
  
 次の表は、さまざまなシナリオのスコアの割り当てを示しています。  
  
|プールされた接続と要求の間の接続属性の比較|参加/参加解除なし|追加の参加を必要とします/ 参加解除|  
|---------------------------------------------------------------------------------------|-----------------------------------|----------------------------------------------|  
|カタログ(SQL_ATTR_CURRENT_CATALOG)が異なる|60|50|  
|接続属性の一部は異なりますが、カタログは同じ|90|70|  
|完全に一致するすべての接続属性|100|80|  
  
## <a name="sequence-diagram"></a>シーケンス図  
 このシーケンス図は、このトピックで説明する基本的なプーリングメカニズムを示しています。 これは[、SQLドライバ接続](../../../odbc/reference/syntax/sqldriverconnect-function.md)の使用のみを示していますが[、SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)のケースは似ています。  
  
 ![シーケンス図](../../../odbc/reference/develop-driver/media/odbc_seq_dia.gif "odbc_seq_dia")  
  
## <a name="state-diagram"></a>状態ダイアグラム  
 この状態ダイアグラムは、このトピックで説明する接続情報トークン オブジェクトを示しています。 図は[SQL ドライバー接続](../../../odbc/reference/syntax/sqldriverconnect-function.md)のみを示していますが[、SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)のケースは似ています。 ドライバー マネージャーは、エラーを処理する必要がありますいつでも、ドライバー マネージャーは、任意の状態の[SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)を呼び出すことができます。  
  
 ![状態の図](../../../odbc/reference/develop-driver/media/odbc_state_diagram.gif "odbc_state_diagram")  
  
## <a name="see-also"></a>参照  
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC サービス プロバイダー インターフェイス (SPI) リファレンス](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md)
