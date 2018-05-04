---
title: RDS アプリケーションを保護する |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS security [ADO]
ms.assetid: 82fb1330-d6c6-4c17-ad3e-d417ff822b25
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 60cb8cde92d116344a99aea1e55d391906096548
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="securing-rds-applications"></a>RDS アプリケーションのセキュリティ保護
このトピックでは rds. のセキュリティについて  
  
> [!IMPORTANT]
>  Windows 8 および Windows Server 2012 から始まり、RDS サーバー コンポーネントは含まれなく Windows オペレーティング システムで (Windows 8 を参照し、 [Windows Server 2012 の互換性クックブック](https://www.microsoft.com/en-us/download/details.aspx?id=27416)詳細については)。 RDS クライアント コンポーネントが Windows の将来のバージョンで削除されます。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。 RDS を使用するアプリケーションに移行する必要があります[WCF Data Service](http://go.microsoft.com/fwlink/?LinkId=199565)です。  
  
## <a name="microsoft-internet-explorer-security-issues"></a>Microsoft Internet Explorer のセキュリティの問題  
 新しいセキュリティが強化された Microsoft Internet Explorer に追加された、ADO および RDS オブジェクトは、「安全な」モード環境でのみ実行しているに制限されます。 これには、別のゾーン、セキュリティ レベル、動作の制限、安全でない操作は、これらの問題を認識しているセキュリティ設定のカスタマイズが必要です。  
  
## <a name="security-and-your-web-server"></a>セキュリティと Web サーバー  
 使用する場合、 [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)インターネットの Web サーバー上のオブジェクト、これは、潜在的なセキュリティ リスクことに注意してください。 有効なデータ ソース名 (DSN)、ユーザー ID とパスワード情報を取得する外部ユーザーには、そのデータ ソースにクエリを送信するページを作成できます。 データ ソースへのアクセスが制限よりを実行する場合に、1 つのオプションが登録を解除し、削除されて、 **RDSServer.DataFactory** (msadcf.dll) をオブジェクトを代わりにハード コーディングされたクエリとカスタム ビジネス オブジェクトを使用します。  
  
 RDSServer.DataFactory オブジェクトを使用するセキュリティへの影響の詳細については、Microsoft Security Web サイトで Microsoft セキュリティ情報の MS99 025 を参照してください。  
  
## <a name="client-impersonation-and-security"></a>クライアントの偽装とセキュリティ  
 場合、**パスワード認証**(Windows NT 4.0) 用の Windows NT チャレンジ/レスポンス認証または統合 Windows 認証 (Windows 2000 の場合)、IIS Web サーバーのプロパティを設定し、ビジネス オブジェクトは、クライアントのセキュリティ コンテキストで呼び出されます。 これは、HTTP 経由でクライアントの偽装を許可する RDS 1.5 の新機能です。 このモードで作業しているときに Web サーバー (IIS) へのログオンには匿名ではありませんが、ユーザー ID とクライアント コンピューターが実行されているパスワードを使用します。 ODBC Dsn は、信頼関係接続を使用する設定は、SQL Server などのデータベースへのアクセスは、クライアントのセキュリティ コンテキストでします。 データベースが、IIS と同じコンピューター上にある場合にのみ有効ですがクライアントの資格情報は、まだ別のコンピューターに引き継がれますことはできません。  
  
 例については、クライアント、John Doe, userid ="JohnD"とパスワード =「シークレット」が、クライアント コンピューターにログオンします。 アクセスする必要があるブラウザー ベースのアプリケーションを実行した、 **RDSServer.DataFactory**を作成するオブジェクト、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)"MyServer"のコンピューターで SQL クエリを実行して IIS を実行します。 MyServer、Windows NT Server 4.0 を実行するシステムが Windows NT チャレンジ/レスポンス認証を使用する設定、その ODBC DSN が「を使用して信頼された接続」選択されている、サーバーにも、SQL Server データ ソースが含まれています。 Web サーバーで要求を受信するととき、に、ユーザー ID とパスワードをクライアントを要求します。 したがって、要求が MyServer としてログオン"JohnD"から IUSER_MyServer (既定である匿名パスワード認証がオンの場合) ではなく「シークレット」/です。 同様に、"JohnD"SQL Server にログオンするときに使用するには、「シークレット」/です。  
  
 その結果、IIS Windows NT チャレンジ/レスポンス認証モードは、ユーザーがデータベースにログオンするために必要なユーザー ID とパスワード情報を明示的に要求されることがなく作成する HTML ページを使用します。 IIS 基本認証が使用されている場合、これが必要な場合もします。  
  
## <a name="password-authentication"></a>パスワード認証  
 RDS が 3 つのパスワードの認証モードのいずれかで実行されている IIS Web サーバーと通信できる: 匿名、基本、または NT チャレンジ/レスポンス認証 (Windows 2000 で統合 Windows 認証と呼ばれます)。 これらの設定は、Web サーバーがクライアント コンピューターにある NT Web サーバー上の明示的なアクセス特権を必要とするなど、アクセスを制御する方法を定義します。


