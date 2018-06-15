---
title: Microsoft JDBC Driver for SQL Server のサポート マトリックス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c5769e67-99f7-4bc1-a4fa-8941dad33d35
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1aceb8c6c7077236d8bf7dcf4794a894adc16030
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32832807"
---
# <a name="microsoft-jdbc-driver-for-sql-server-support-matrix"></a>Microsoft SQL Server 用 JDBC Driver のサポート表
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このページには、Microsoft SQL Server 用 JDBC Driver のサポート表とサポート ライフサイクル ポリシーがあります。  
  
## <a name="microsoft-jdbc-driver-support-lifecycle-matrix-and-policy"></a>Microsoft JDBC Driver サポート ライフサイクルの表とポリシー  
 マイクロソフト サポート ライフサイクル (MSL) ポリシーでは、マイクロソフト製品のサポート ライフサイクルを理解しやすくする、予測可能な情報を提供しています。 JDBC ドライバーのバージョン 3.0、4.x および 6.x リリース日 5 年ドライバーからメイン ストリーム サポートがあります。 メインストリーム サポートについては、マイクロソフト サポート ライフサイクルの Web サイトで定義されています。  
  
 延長サポートとカスタム サポートのオプションは、Microsoft JDBC Driver では使用できません。  
    
 次の Microsoft JDBC Driver は、表示されているサポートの終了日までサポートされます。  
  
|ドライバー名|ドライバー パッケージのバージョン|該当する JAR(s)|メイン ストリーム サポートの終了|
|-|-|-|-|  
|Microsoft SQL Server 用 JDBC Driver 6.4|6.4|mssql-jdbc-6.4.0.jre9.jar<br> mssql-jdbc-6.4.0.jre8.jar<br> mssql-jdbc-6.4.0.jre7.jar|2023 年 1 月 22日|    
|Microsoft JDBC Driver 6.2 for SQL Server|6.2|mssql-jdbc-6.2.2.jre8.jar<br> mssql-jdbc-6.2.2.jre7.jar|2022 年 6 月 30日|    
|Microsoft SQL Server 用 JDBC Driver 6.0|6.0|sqljdbc42.jar<br>sqljdbc41.jar|2021 年 7 月 14日|    
|Microsoft SQL Server 用 JDBC Driver 4.2|4.2|sqljdbc42.jar<br>sqljdbc41.jar|2020 年 8 月 24 日|  
|Microsoft SQL Server 用 JDBC Driver 4.1|4.1|sqljdbc41.jar|2019 年 12 月 12日|  
  
 次の Microsoft JDBC ドライバーはサポートされなくなりました。  
 
|ドライバー名|ドライバー パッケージのバージョン|メイン ストリーム サポートの終了|  
|-|-|-|
|Microsoft SQL Server 用 JDBC Driver 4.0|4.0|2017 年 3 月 6 日|  
|Microsoft SQL Server JDBC Driver 3.0|3.0|2015 年 4 月 23 日|  
|Microsoft SQL Server JDBC Driver 2.0|2.0|2012 年 12 月 31 日|  
|Microsoft SQL Server 2005 JDBC ドライバー 1.2|1.2|2011 年 6 月 25 日|  
|Microsoft SQL Server 2005 JDBC Driver 1.1|1.1|2011 年 6 月 25 日|  
|Microsoft SQL Server 2005 JDBC Driver 1.0|1.0|2011 年 6 月 25 日|  
|Microsoft SQL Server 2000 JDBC Driver|2000|2010 年 7 月 9 日|  
  
## <a name="sql-version-compatibility"></a>SQL バージョンの互換性  
  
|ドライバーのバージョン|SQL Server 2008:|SQL Server 2008R2|SQL Server 2012|Azure SQL Database|PDW 2008R2 AU3<sup>4</sup>|SQL Server 2014|SQL Server 2016|SQL Server 2017|Azure SQL のマネージ インスタンス (プライベート プレビューでは拡張)|  
|-|-|-|-|-|-|-|-|-|-|
|6.4|×|Y|Y|Y|Y|Y|Y|Y|Y|  
|6.2|Y|Y|Y|Y|Y|Y|Y|Y|×|
|6.1|Y|Y|Y|Y|Y|Y|Y|×|×|
|6.0|Y|Y|Y|Y|Y|Y|Y|×|×|
|4.2|Y|Y|Y|Y|Y|Y|Y|×|×|
|4.1|Y|Y|Y|Y|Y|Y|Y|×|×|
|4.0|Y|Y|Y|Y|Y|Y|Y|×|×|
|3.0|Y|Y|Y<sup>1</sup>|Y<sup>2</sup>|×|Y<sup>5</sup>|×|×|×|
|2.0|Y<sup>3</sup>|Y<sup>3</sup>|×|×|×|×|×|×|×|
|1.2|Y<sup>3</sup>|×|×|×|×|×|×|×|×|
|1.1|×|×|×|×|×|×|×|×|×|  
|1.0|×|×|×|×|×|×|×|×|×|  
|2000|×|×|×|×|×|×|×|×|×|  
  
 <sup>1</sup>Microsoft SQL Server JDBC Driver version 3.0 は、下位クライアントとして SQL Server 2012 に接続できます。  
  
 <sup>2</sup>修正プログラムとして 3.0 のドライバーに Azure SQL Database のサポートが導入されました。 Azure SQL Database のお客様は、最新バージョンのドライバーを使用することをおすすめします。  
  
 <sup>3</sup>Microsoft SQL Server JDBC Driver version 2.0 および Microsoft SQL Server 2005 JDBC Driver version 1.2 下位クライアントとして SQL Server 2008 に接続できます。 下位変換が許可されている場合、アプリケーションはクエリを実行し、新しい SQL Server 2008 データ型 (time、date、datetime2、datetimeoffset、FILESTREAM など) の更新を実行できます。 これらの新しいデータ型を JDBC ドライバーで使用する方法の詳細については、「  [Working with SQL Server 2008 Date/Time Data Types using JDBC Driver (JDBC ドライバーを使用して SQL Server 2008 の日付/時刻データ型を操作する)](http://go.microsoft.com/fwlink/?LinkId=145198) 」および「  [Working with SQL Server 2008 FileStream using JDBC Driver (JDBC ドライバーを使用して SQL Server 2008 の FileStream を操作する](http://go.microsoft.com/fwlink/?LinkId=145199)」をご覧ください。 これらの新しいデータ型の下位互換性の詳細については、SQL Server オンライン ブックの「  [日時データの使用](http://go.microsoft.com/fwlink/?LinkId=145211)」および「  [FILESTREAM のサポート](http://go.microsoft.com/fwlink/?LinkId=145212) 」トピックをご覧ください。  
  
 <sup>4</sup>Microsoft JDBC Driver と並列データ ウェアハウス間の接続のサポートで初めて導入されました、Microsoft JDBC Driver 4.0 for SQL Server と Microsoft SQL Server 2008 R2 並列データ ウェアハウス アプライアンス更新プログラム 3 です。  
  
 <sup>5</sup>Microsoft SQL Server JDBC Driver version 3.0 は、下位クライアントとして SQL Server 2014 に接続できます。  
  
## <a name="java-and-jdbc-specification-support"></a>Java と JDBC の仕様のサポート  
  
|JDBC ドライバーのバージョン|JRE のバージョン|JDBC API のバージョン| 
|-|-|-|  
|6.4|1.7、1.8、1.9|4.1、4.2、4.3 (部分的)|  
|6.2|1.7, 1.8|4.1, 4.2|  
|6.1|1.7, 1.8|4.1, 4.2|  
|6.0|1.7, 1.8|4.1, 4.2|  
|4.2|1.7, 1.8|4.1, 4.2|  
|4.1|1.7|4.0|  
|4.0|1.5, 1.6, 1.7|3.0, 4.0|  
|3.0|1.5, 1.6,|3.0, 4.0|  
|2.0|1.5, 1.6|3.0, 4.0|  
|1.2|1.4, 1.5, 1.6|3.0|  
|1.1|1.4|3.0|  
|1.0|1.4|3.0|  
|2000|1.4|3.0|  
  
## <a name="supported-operating-systems"></a>サポートされるオペレーティング システム  
 Microsoft JDBC Driver は、Java 仮想マシン (JVM) の使用をサポートするすべてのオペレーティング システムで機能するように設計されています。 一般的に使用されるプラットフォームには、Windows 10、Windows 8.1、Windows 8、Windows 7、Windows Server 2008 R2、Windows Vista、Linux、Unix、AIX、MacOS などがあります。  
  
 JDBC 製品チームは、Windows、Sun Solaris、SUSE Linux、Red Hat Linux でドライバーをテストしています。  カスタマー サポートは、すべてのプラットフォームのお客様にご利用いただけますが、Windows などのプラットフォームで問題の再現をお客様にお願いする場合があります。  
  
## <a name="application-server-support"></a>アプリケーション サーバーのサポート  
 Microsoft SQL Server 用 JDBC Driver は、さまざまなアプリケーション サーバーでテストされています。  これらの製品と互換性のあるドライバー バージョンの詳細情報については、ご利用のアプリケーション サーバーの製造元にお問い合わせください。  
  
  
