# KapwingAPI
.NET API Library for kapwing.com

`Download:`[https://github.com/loudKode/KapwingAPI/releases](https://github.com/loudKode/KapwingAPI/releases)
# Functions:
```vb.net
    Function Video2GIF(VideoUrl As String, Optional startT As Single = Nothing, Optional endT As Single = Nothing) As Task(Of JSON.JSON_TrimVideoFinal)
    Function ResizeVideo(VideoUrl As String, ResizeTemplate As KClient.ResizeTemplateEnum, BackgroundColor As Drawing.Color, Optional startT As Single = Nothing, Optional endT As Single = Nothing) As Task(Of JSON.JSON_TrimVideoFinal)
    Function TrimVideo(VideoUrl As String, startT As Single, endT As Single) As Task(Of JSON.JSON_TrimVideoFinal)
    Function SpeedVideo(VideoUrl As String, Speed As KClient.SpeedEnum, Optional startT As Single = Nothing, Optional endT As Single = Nothing) As Task(Of JSON.JSON_TrimVideoFinal)
    Function OperationStatus(VideoID As String) As Task(Of JSON.JSON_OperationStatus)
    Function DownloadVideoAsStream(VideoID As String, Optional ReportCls As IProgress(Of ReportStatus) = Nothing, Optional _proxi As ProxyConfig = Nothing, Optional TimeOut As Integer = 60, Optional token As Threading.CancellationToken = Nothing) As Task(Of IO.Stream)
    Function DownloadVideo(VideoID As String, FileSaveDir As String, FileName As String, Optional ReportCls As IProgress(Of ReportStatus) = Nothing, Optional _proxi As ProxyConfig = Nothing, Optional TimeOut As Integer = 60, Optional token As Threading.CancellationToken = Nothing) As Task
    Function RenameVideo(VideoID As String, NewName As String) As Task(Of Boolean)
    Function VideoMetadata(VideoID As String) As Task(Of JSON.VideoMetaData)
    Function Image2Video(ImageUrl As String, VideoDurationInSec As Integer, VideoRatio As KClient.VideoRatioEnum, VideoPosition As KClient.VideoPositionEnum) As Task(Of JSON.JSON_TrimVideoFinal)
    Function ListVideos() As Task(Of JSON.JSON_ListVideos)
    Function DeleteVideo(VideoID As String) As Task(Of Boolean)
    Function OriginalVideoMetadata(VideoUrl As String) As Task(Of JSON.JSON_OriginalVideoMetadata)
    Function UserInfo() As Task(Of JSON.JSON_UserInfo)
```

# Example:
```vb.net
Dim cLENT As KapwingAPI.IClient = New KapwingAPI.KClient("", "")
Dim RSLT = Await cLENT.UserInfo
Dim RSLT = Await cLENT.OriginalVideoMetadata("https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_2mb.mp4")
Dim RSLT = Await cLENT.TrimVideo("https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_2mb.mp4", 5.03, 7.49)
Dim RSLT = Await cLENT.OperationStatus(videoid.Text)
Dim RSLT = Await cLENT.ListVideos()
Dim RSLT = Await cLENT.DeleteVideo(videoid.Text)
Dim RSLT = Await cLENT.Image2Video("https://cdn.pixabay.com/photo/2017/02/01/22/02/mountain-landscape-2031539_960_720.jpg", 1, KapwingAPI.KClient.VideoRatioEnum.Facebook, KapwingAPI.KClient.VideoPositionEnum.fit)
Dim RSLT = Await cLENT.SpeedVideo("https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_2mb.mp4", KapwingAPI.KClient.SpeedEnum.x0_25)
Dim RSLT = Await cLENT.ResizeVideo("https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_2mb.mp4", KapwingAPI.KClient.ResizeTemplateEnum.Facebook, Color.FromArgb(99, 221, 161), 5.03, 7.49)
Dim RSLT = Await cLENT.RenameVideo("xxxxxxxxxxxxxxxx", "gogo")
Dim RSLT = Await cLENT.VideoMetadata(videoid.Text)
Dim RSLT = Await cLENT.Video2GIF("https://sample-videos.com/video123/mp4/720/big_buck_bunny_720p_2mb.mp4", 5.03, 7.49)
```
