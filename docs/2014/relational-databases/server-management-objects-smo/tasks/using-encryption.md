---
title: 暗号化を使用して |Microsoft ドキュメント
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
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
caps.latest.revision: 25
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: dc5e06d1b63429830fe7216ab28c4ed45f0279a4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070688"
---
# <a name="using-encryption"></a>暗号化の使用
  SMO では、サービス マスター _ キーがで表される、<xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey>オブジェクト。 これには、参照によって、<xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A>のプロパティ、<xref:Microsoft.SqlServer.Management.Smo.Server>オブジェクト。 使用して再生成することができます、<xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A>メソッドです。  
  
 データベース マスター _ キーがで表される、<xref:Microsoft.SqlServer.Management.Smo.MasterKey>オブジェクト。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A>プロパティは、データベース マスター _ キーはサービス マスター _ キーによって暗号化されているかどうかを示します。 master データベース内の暗号化されたコピーは、データベース マスター キーが変更されるたびに自動的に更新されます。  
  
 キーの暗号化を使用してサービスを削除することは、<xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A>メソッドとパスワードを使用して、データベース マスター _ キーを暗号化します。 この場合、セキュリティで保護された秘密キーにアクセスする前に、データベース マスター キーを明示的に開く必要があります。  
  
 インスタンスにデータベースがアタッチされるときに[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]、データベース マスター _ キーのパスワードを指定するかを実行する必要があります、<xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A>暗号化されていないデータベース マスター _ キーのコピーをサービスでの暗号化に使用できるようにするメソッドマスター _ キー。 データベース マスター キーを明示的に開く必要性を回避するには、この手順をお勧めします。  
  
 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A>メソッドは、データベース マスター _ キーを再生成します。 データベース マスター キーが再生成されると、このデータベース マスター キーで暗号化されたすべてのキーの暗号化が解除され、これらのキーが新しいデータベース マスター キーで暗号化されます。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A>メソッドは、サービス マスター _ キーによって、データベース マスター _ キーの暗号化を削除します。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> は、サービス マスター キーを使用してマスター キーのコピーを暗号化し、現在のデータベースおよび master データベースの両方に格納します。  
  
 SMO では、証明書がによって表される、<xref:Microsoft.SqlServer.Management.Smo.Certificate>オブジェクト。 <xref:Microsoft.SqlServer.Management.Smo.Certificate>オブジェクトには、公開キー、サブジェクトの名前、有効期間、および発行者に関する情報を指定するプロパティです。 使用して、証明書にアクセスする権限が制御されます、 `Grant`、`Revoke`と`Deny`メソッドです。  
  
## <a name="example"></a>例  
 次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。 詳細については、次を参照してください。 [Visual Studio .NET で Visual Basic SMO プロジェクトを作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)と[Visual C を作成する&#35;Visual Studio .NET での SMO プロジェクト](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)です。  
  
## <a name="adding-a-certificate-in-visual-basic"></a>Visual Basic での証明書の追加  
 コード例では、暗号化パスワードを持つ簡単な証明書を作成します。 その他のオブジェクトとは異なり、<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>メソッドいくつかのオーバー ロードがあります。 この例で使用するオーバーロードは、暗号化パスワードを持つ新しい証明書を作成しています。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCertificate1](SMO How to#SMO_VBCertificate1)]  -->  
  
## <a name="adding-a-certificate-in-visual-c"></a>Visual C# での証明書の追加  
 コード例では、暗号化パスワードを持つ簡単な証明書を作成します。 その他のオブジェクトとは異なり、<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>メソッドいくつかのオーバー ロードがあります。 この例で使用するオーバーロードは、暗号化パスワードを持つ新しい証明書を作成しています。  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>PowerShell での証明書の追加  
 コード例では、暗号化パスワードを持つ簡単な証明書を作成します。 その他のオブジェクトとは異なり、<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A>メソッドいくつかのオーバー ロードがあります。 この例で使用するオーバーロードは、暗号化パスワードを持つ新しい証明書を作成しています。  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate  
  
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -argumentlist $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")  
  
```  
  
## <a name="see-also"></a>参照  
 [暗号化キーを使用します。](using-encryption.md)  
  
  