---
title: "Microsoft R Server (スタンドアロン) の概要 | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: r-server
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52347d0d-ce60-4bb8-98d2-6163e87716b0
caps.latest.revision: 21
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fc7874c6900474c7c2f3d927183616b2f5e69699
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="getting-started-with-microsoft-r-server-standalone"></a>Microsoft R Server の概要 (スタンドアロン)
  Microsoft R Server (スタンドアロン) を使用すると、一般的なオープン ソースの R 言語を利用して、高パフォーマンスの分析ソリューションを作成したり、他のビジネス アプリケーションと統合したりできます。  

  
## <a name="install-microsoft-r-server"></a>Microsoft R Server をインストールする 

アプリケーションで SQL Server のデータを使用する必要があるかどうかによって、Microsoft R Server のインストール方法が異なります。 アプリケーションで使用する必要がある場合は、SQL Server セットアップを使用してインストールしてください。 SQL Server のデータを使用しなかったり、データベース内で R コードを実行する必要がない場合は、SQL Server セットアップと新しいスタンドアロン インストーラーのどちらも使用できます。
 
 
+ SQL Server セットアップから Microsoft R Server (スタンドアロン) をインストールします。 R Server に R バイナリの別のインスタンスが作成され、SQL Server Enterprise Edition のサポート ポリシーによってインスタンスが許諾されます。 詳しくは、「[Create a Standalone R Server (スタンドアロン R Server の作成)](../../advanced-analytics/r-services/create-a-standalone-r-server.md)」をご覧ください。  

+ Microsoft の最新のソフトウェア ライフサイクル サポート ポリシーを使用する Microsoft R Server の新しいインスタンスを作成するには、新しい Windows スタンドアロン インストーラーを使用します。 詳細については、[Microsoft R Server for Windows の実行](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)に関するページを参照してください。

+ R Server (スタンドアロン) の既存のインスタンス、またはアップグレードが必要な R Services がある場合は、更新用に Windows ベースのインストーラーをダウンロードして実行する必要があります。 詳細については、[Microsoft R Server for Windows の実行](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)に関するページを参照してください。
  
## <a name="install-additional-r-tools"></a>追加の R Tools をインストールする  

 無償の [Microsoft R Client](http://aka.ms/rclient/download) (ダウンロード) をお勧めします。  

 また、お好みの R 開発環境ソリューションを使用して、SQL Server R Services や Microsoft R Server のソリューションを開発できます。 詳細については、「[Setup or Configure R Tools (R ツールのセットアップまたは構成)](../../advanced-analytics/r-services/setup-or-configure-r-tools.md)」をご覧ください。 
 

### <a name="location-of-r-server-binaries"></a>R Server バイナリの場所

Microsoft R Server のインストールに使用する方法によって、既定の場所が異なります。 好みの開発環境を使用する前に、R ライブラリをインストールした場所を確認しておきます。

+ 新しい Windows インストーラーを使用してインストールされた Microsoft R Server

  `C:\Program Files\Microsoft\R Server\R_SERVER`

+ SQL Server セットアップを使用してインストールされた R Server (スタンドアロン)

  `C:\Program Files\Microsoft SQL Server\130\R_SERVER`

+ R Services (In-Database)

  `C:\Program Files\Microsoft SQL Server\<instance_name>\R_SERVICES`
      
## <a name="start-using-r-on-microsoft-r-server"></a>Microsoft R Server で R を使用する  

 サーバー コンポーネントを設定し、R Server バイナリを使用するように R 統合開発環境 (IDE) を構成したら、新しい API (RevoScaleR パッケージ、MicrosoftML、olapR など) を使用してソリューションを開発できます。
    
R Server の概要については、MSDN ライブラリの [R Server の概要](https://msdn.microsoft.com/microsoft-r/microsoft-r-get-started-node)に関するガイドをご覧ください。   
  
-   [ScaleR](https://msdn.microsoft.com/microsoft-r/scaler-getting-started): R ソリューションに高いパフォーマンスとスケーリングを提供する、再頒布可能な分析関数のコレクションを探索します。 最も一般的な R モデリング パッケージ (K-平均法クラスタリング、デシジョン ツリー、デシジョン フォレストなど) の並列化可能なバージョンの多くと、データ操作のツールを含みます。 詳細については、「[Explore R and ScaleR in 25 Functions](https://msdn.microsoft.com/microsoft-r/microsoft-r-getting-started-tutorial) (25 の関数で R と ScaleR を探索する)」を参照してください。  
    
- [MicrosoftML](https://msdn.microsoft.com/library/mt790482.aspx): MicrosoftML パッケージは、Microsoft が開発した高速でスケーラブルな新しい機械学習アルゴリズムと変換のセットです。 詳細については、[MicrosoftML 関数](https://msdn.microsoft.com/microsoft-r/microsoftml/microsoftml)に関するページをご覧ください。
  


  
## <a name="see-also"></a>参照  
 [SQL Server R Services の概要](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)  
  
  

