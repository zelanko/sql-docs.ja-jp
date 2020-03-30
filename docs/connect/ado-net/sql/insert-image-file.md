---
title: ファイルからのイメージの挿入
description: ファイルの画像を操作する方法について説明します。
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 35900aa2-5615-4174-8212-ba184c6b82fb
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 9d80f5eec2c33fed635c18937185e2e21798e93b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896720"
---
# <a name="inserting-an-image-from-a-file"></a>ファイルからのイメージの挿入

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

バイナリ ラージ オブジェクト (BLOB) は、データ ソースのフィールドの種類に応じて、バイナリ データまたは文字データとしてデータベースに書き込むことができます。 BLOB は、`text`、`ntext`、および `image` データ型をのことを指す一般用語であり、通常はドキュメントと画像が含まれます。  
  
BLOB 値をデータベースに書き込むには、適切な INSERT または UPDATE ステートメントを実行し、入力パラメーターとして BLOB 値を渡します。 BLOB を SQL Server `text` フィールドなどのテキストとして格納する場合は、BLOB を文字列パラメーターとして渡すことができます。 BLOB を SQL Server `image` フィールドなどのバイナリ形式で格納する場合は、`byte` 型の配列をバイナリ パラメーターとして渡すことができます。
  
## <a name="example"></a>例  
次のコード例では、Northwind データベースの Employees テーブルに従業員情報を追加します。 従業員の写真がファイルから読み取られ、テーブルの Photo フィールド (画像フィールド) に追加されます。  
  
```csharp  
public static void AddEmployee(  
  string lastName,   
  string firstName,   
  string title,   
  DateTime hireDate,   
  int reportsTo,   
  string photoFilePath,   
  string connectionString)  
{  
  byte[] photo = GetPhoto(photoFilePath);  
  
  using (SqlConnection connection = new SqlConnection(  
    connectionString))  
  
  SqlCommand command = new SqlCommand(  
    "INSERT INTO Employees (LastName, FirstName, " +  
    "Title, HireDate, ReportsTo, Photo) " +  
    "Values(@LastName, @FirstName, @Title, " +  
    "@HireDate, @ReportsTo, @Photo)", connection);   
  
  command.Parameters.Add("@LastName",    
     SqlDbType.NVarChar, 20).Value = lastName;  
  command.Parameters.Add("@FirstName",   
      SqlDbType.NVarChar, 10).Value = firstName;  
  command.Parameters.Add("@Title",       
      SqlDbType.NVarChar, 30).Value = title;  
  command.Parameters.Add("@HireDate",   
       SqlDbType.DateTime).Value = hireDate;  
  command.Parameters.Add("@ReportsTo",   
      SqlDbType.Int).Value = reportsTo;  
  
  command.Parameters.Add("@Photo",  
      SqlDbType.Image, photo.Length).Value = photo;  
  
  connection.Open();  
  command.ExecuteNonQuery();  
  }  
}  
  
public static byte[] GetPhoto(string filePath)  
{  
  FileStream stream = new FileStream(  
      filePath, FileMode.Open, FileAccess.Read);  
  BinaryReader reader = new BinaryReader(stream);  
  
  byte[] photo = reader.ReadBytes((int)stream.Length);  
  
  reader.Close();  
  stream.Close();  
  
  return photo;  
}  
```  
  
## <a name="next-steps"></a>次のステップ
- [SQL Server のバイナリ データと大きな値のデータ](sql-server-binary-large-value-data.md)
