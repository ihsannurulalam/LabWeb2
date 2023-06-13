
```bash
    CREATE DATABASE lab_ci4;
```
# Create Code Artikel
```bash
public function add()
{
// validasi data.
$validation = \Config\Services::validation();
$validation->setRules(['judul' => 'required']);
$isDataValid = $validation->withRequest($this->request)->run();
if ($isDataValid)
{
$file = $this->request->getFile('gambar');
$file->move(ROOTPATH . 'public/gambar');
$artikel = new ArtikelModel();
$artikel->insert([
'judul' => $this->request->getPost('judul'),
'isi' => $this->request->getPost('isi'),
'slug' => url_title($this->request->getPost('judul')),
'gambar' => $file->getName(),
]);
return redirect('admin/artikel');
}
$title = "Tambah Artikel";
return view('artikel/form_add', compact('title'));
}
```
# Form add.php
```bash
<p>
<input type="file" name="gambar">
</p>
```

# Sesuaikan tag form dengan menambahkan ecrypt type seperti berikut.
```bash
<form action="" method="post" enctype="multipart/form-data">
```




