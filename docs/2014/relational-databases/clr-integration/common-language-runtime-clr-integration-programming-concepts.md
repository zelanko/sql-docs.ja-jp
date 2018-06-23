---
title: 共通言語ランタイム (CLR) 統合のプログラミングの概念 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- CLR [SQL Server] See common language runtime [SQL Server]
- Database Engine [SQL Server], .NET Framework
- .NET Framework [SQL Server], Database Engine programming
- common language runtime [SQL Server]
- .NET Framework [SQL Server]
ms.assetid: 951bf851-3e6e-4361-ae6a-2bcd5b837ebd
caps.latest.revision: 56
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3f508cdada9905c2a8ec322319df58cb5504af14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173735"
---
# <a name="common-language-runtime-clr-integration-programming-concepts"></a>CLR (共通言語ランタイム) 統合のプログラミング概念
  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] には、.NET Framework for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows の CLR (共通言語ランタイム) コンポーネントが統合されました。 つまり、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic .NET や [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# などの .NET Framework 言語を使用して、ストアド プロシージャ、トリガー、ユーザー定義型、ユーザー定義関数、ユーザー定義集計、およびストリーミング テーブル値関数を記述できるようになります。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] における CLR プログラミングのためのコア機能は、Microsoft.SqlServer.Server 名前空間に存在します。 ただし、Microsoft.SqlServer.Server 名前空間については、.NET Framework SDK ドキュメントをご覧ください。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックには、このドキュメントが含まれていません。  
  
> [!IMPORTANT]  
>  既定では、.NET Framework は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] と共にインストールされますが、.NET Framework SDK はインストールされません。 SDK がコンピューターにインストールされていない場合やオンライン ブックに含まれていない場合は、このセクションにある SDK のコンテンツへのリンクが機能しません。 .NET Framework SDK をインストールしてください。 インストールした後、SDK をオンライン ブック コレクションと目次に追加」の指示に従って[、.NET Framework SDK をインストールする](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)です。  
  
 次の表は、このセクションのトピックを一覧表示します。  
  
 [共通言語ランタイム&#40;CLR&#41;の統合の概要](common-language-runtime-integration-overview.md)  
 CLR の概要を簡単に紹介し、このテクノロジが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で使用される方法と理由について説明します。 CLR を使用してデータベース オブジェクトを作成する利点についても説明します。  
  
 [アセンブリ &#40;データベース エンジン&#41;](assemblies-database-engine.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではなく、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) がサポートするマネージ コード言語の 1 つを使用して作成された関数、ストアド プロシージャ、トリガー、ユーザー定義集計、ユーザー定義型の配置に、[!INCLUDE[tsql](../../../includes/tsql-md.md)] でアセンブリがどのように使用されるかについて説明します。  
  
 [共通言語ランタイムとデータベース オブジェクトの構築&#40;CLR&#41;統合](database-objects/building-database-objects-with-common-language-runtime-clr-integration.md)  
 CLR を使用して作成できるオブジェクトの種類について説明し、CLR データベース オブジェクトの作成要件を確認します。  
  
 [CLR データベース オブジェクトからのデータ アクセス](data-access/data-access-from-clr-database-objects.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに格納されているデータに CLR ルーチンからアクセスする方法について説明します。  
  
 [CLR 統合のセキュリティ](security/clr-integration-security.md)  
 CLR 統合のセキュリティ モデルについて説明します。  
  
 [CLR データベース オブジェクトのデバッグ](debugging-clr-database-objects.md)  
 CLR データベース オブジェクトをデバッグする場合の制限事項と要件について説明します。  
  
 [CLR データベース オブジェクトの配置](deploying-clr-database-objects.md)  
 実稼働サーバーへのアセンブリの配置について説明します。  
  
 [CLR 統合アセンブリの管理](assemblies/managing-clr-integration-assemblies.md)  
 CLR 統合のアセンブリの作成および削除方法について説明します。  
  
 [マネージ データベース オブジェクトの監視とトラブルシューティング](monitoring-and-troubleshooting-managed-database-objects.md)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で実行されるマネージ データベース オブジェクトとアセンブリの監視およびトラブルシューティングに使用できるツールに関する情報を提供します。  
  
 [CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例](../../database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
 CLR オブジェクトを使用する使用シナリオとコード サンプルについて説明します。  
  
## <a name="see-also"></a>参照  
 [アセンブリ&#40;データベース エンジン&#41;](assemblies-database-engine.md)   
 [.NET Framework SDK のインストール](http://technet.microsoft.com/library/bb686823\(v=SQL.105\).aspx)  
  
  