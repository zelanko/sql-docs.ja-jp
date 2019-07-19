---
title: SQL Server Native Client のシステム要件 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- system requirements [SQL Server Native Client]
- data access [SQL Server Native Client], system requirements
- SQL Server Native Client, system requirements
- SQLNCLI, system requirements
ms.assetid: 1c8e2f8a-a440-44da-8e3a-af632d34c52c
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8af6065a08cc85c7bdc2c36c6032506ba6d56c57
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031763"
---
# <a name="system-requirements-for-sql-server-native-client"></a>SQL Server Native Client のシステム要件
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のデータ アクセス機能 (MARS など) を使用するには、次のソフトウェアがインストールされている必要があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (クライアント)  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス (サーバー)  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client には、Windows インストーラー 3.0 が必要です。 Windows インストーラー 3.0 は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows オペレーティング システムに既にインストールされています。 他のすべてのプラットフォームには、明示的にインストールする必要があります。 詳細については、次を参照してください。 [Windows Installer 3.0 Redistributable](https://go.microsoft.com/fwlink/?LinkId=46459)します。  
  
> [!NOTE]  
>  このソフトウェアは、必ず管理者特権でログオンしてからインストールしてください。  
  
## <a name="operating-system-requirements"></a>必要なオペレーティング システム  
 サポートするオペレーティング システムの一覧については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client を参照してください[SQL Server Native Client のサポート ポリシー](../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md)します。  
  
## <a name="sql-server-requirements"></a>SQL Server の要件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータにアクセスするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスがインストールされている必要があります。  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] は、MDAC、Windows Data Access Components、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のすべてのバージョンからの接続をサポートします。 古いクライアント バージョンで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続する場合、クライアントで認識されないサーバーのデータ型は、クライアント バージョンと互換する型にマップされます。 詳細については、このトピックの「クライアント バージョンのデータ型の互換性」をご覧ください。  
  
## <a name="cross-language-requirements"></a>言語間の要件  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の英語版は、サポートされているオペレーティング システムであれば、そのすべてのローカライズ版でもサポートされます。 ローカライズ版[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client が、ローカライズされたのと同じ言語であるローカライズされたオペレーティング システムでサポートされている[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client のバージョン。 ローカライズ版[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client はサポートされているオペレーティング システムの英語版のサポートも、一致する言語設定がインストールされている限り、します。  
  
 アップグレードの要件を次に示します。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client の英語版は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のどのローカライズ版にもアップグレードできます。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のローカライズ版は、同じ言語にローカライズされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client にアップグレードできます。  
  
-   ローカライズ版[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client の英語版にアップグレードできます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client のローカライズ版は、異なる言語にローカライズされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client にはアップグレードできません。  
  
## <a name="data-type-compatibility-for-client-versions"></a>クライアント バージョンのデータ型の互換性  
 以下の表に示すように、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client は新しいデータ型を、下位クライアントと互換する古いデータ型にマップします。  
  
 OLE DB と ADO アプリケーションで使用できます、 **DataTypeCompatibility**接続文字列キーワードを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]古いデータ型で動作するネイティブ クライアントです。 **DataTypeCompatibility=80** の場合、OLE DB クライアントは TDS (表形式データ ストリーム) バージョンではなく、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] TDS バージョンを使用して接続します。 つまり、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のデータ型の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ではなく、サーバーによって下位変換が実行されます。 またこの場合は、接続で使用可能な機能が、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 機能セットに制限されます。 新しいデータ型または機能を使用しようとすると、API 呼び出し時にすぐに検出されます。無効な要求はサーバーに渡されず、呼び出し元のアプリケーションにエラーが返されます。  
  
 ない**DataTypeCompatibility** ODBC 用のコントロール。  
  
 IDBInfo::GetKeywords は常には影響されません、接続のサーバー バージョンに対応するキーワードの一覧を返します**DataTypeCompatibility**します。  
  
|データ型|SQL Server Native Client<br /><br /> SQL Server 2005|SQL Server Native Client 11.0<br /><br /> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|Windows Data Access Components、MDAC、<br /><br /> DataTypeCompatibility=80 が設定された SQL Server Native Client OLE DB アプリケーション|  
|---------------|--------------------------------------------------|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|  
|CLR UDT (\<= 8Kb)|udt|Udt|Varbinary|  
|varbinary(max)|varbinary|varbinary|イメージ|  
|varchar(max)|varchar|varchar|テキスト|  
|nvarchar(max)|NVARCHAR|NVARCHAR|Ntext|  
|xml|xml|xml|Ntext|  
|CLR UDT (8 KB を超える)|udt|varbinary|イメージ|  
|日付|日付|varchar|Varchar|  
|datetime2|datetime2|varchar|Varchar|  
|datetimeoffset|datetimeoffset|varchar|Varchar|  
|time|time|varchar|Varchar|  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client プログラミング](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [SQL Server Native Client のインストール](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  
