# PopUp-Menu-Android-Kotlin

```
private fun showPopup(v: View) {
        PopupMenu(v.context, v).apply {
            setOnMenuItemClickListener { item ->
                when (item?.itemId) {

                    R.id.edit -> {
                       //peform edit operation
                        true
                    }

                    R.id.delete -> {
                         //perform delete operation
                        true
                    }

                    else -> false
                }
            }
            inflate(R.menu.edit_delete_menu)
            show()
        }
    }
```
