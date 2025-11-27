# Control-sample-collction
import streamlit as st

st.set_page_config(page_title="Registration Form", layout="centered")

st.title("User Registration Form")

# --- Form section ---
with st.form("registration_form"):
    st.header("Personal Information")

    name = st.text_input("Full Name")

    # Woreda options
    woreda_list = [
        "Woreda 01", "Woreda 02", "Woreda 03", "Woreda 04",
        "Woreda 05", "Woreda 06"
    ]
    woreda = st.selectbox("Select Woreda", woreda_list)

    # Kebele options
    kebele_list = [
        "Kebele 01", "Kebele 02", "Kebele 03",
        "Kebele 04", "Kebele 05", "Kebele 06"
    ]
    kebele = st.selectbox("Select Kebele", kebele_list)

    phone = st.text_input("Phone Number")

    st.header("Upload Files")
    photo = st.file_uploader("Upload Photo", type=["jpg", "jpeg", "png"])
    video = st.file_uploader("Upload Video", type=["mp4", "mov"])
    pdf = st.file_uploader("Upload PDF Document", type=["pdf"])

    submitted = st.form_submit_button("Submit")

# --- Result Section ---
if submitted:
    st.success("Registration Submitted Successfully!")

    st.write("### User Details")
    st.write(f"**Name:** {name}")
    st.write(f"**Woreda:** {woreda}")
    st.write(f"**Kebele:** {kebele}")
    st.write(f"**Phone:** {phone}")

    st.write("### Uploaded Files")

    if photo:
        st.image(photo, caption="Uploaded Photo", use_column_width=True)

    if video:
        st.video(video)

    if pdf:
        st.write("PDF Uploaded:")
        st.download_button("Download PDF", pdf, file_name=pdf.name)
